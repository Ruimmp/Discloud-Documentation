---
description: Guia prático para hospedar aplicações Next.js na Discloud.
icon: n
hidden: true
---

# Como hospedar um app Next.js na Discloud

> Guia prático baseado no vídeo "Como hospedar app Next.js facilmente na Discloud" e nos exemplos oficiais da documentação Discloud.

---

## 🧭 Introdução

Este guia passo a passo mostra como preparar, configurar e fazer o deploy de uma aplicação **Next.js** na Discloud.

Existem duas abordagens principais:

- **Opção A (recomendada)** – usar o `next build` + `next start` **sem servidor custom** (apenas o server interno do Next.js).
- **Opção B** – usar um **servidor custom** com **Express**, útil se você precisa de **rotas extras, middlewares customizados ou integrações específicas**.

Além disso, mostramos uma **alternativa com export estático**, ideal para sites puramente estáticos.

{% hint style="info" %}
Este guia assume que você já tem um projeto Next.js funcionando localmente.
{% endhint %}

{% hint style="success" %}
### Regras importantes da Discloud para websites e APIs:

- Um **subdomínio deve ser criado** antes do deploy.
- A aplicação deve **escutar na porta `8080`**.
- Hospedagem de websites/APIs geralmente exige **plano Platinum ou superior**.
  {% endhint %}

---

## 🧱 Pré-requisitos locais

Antes de continuar, você vai precisar:

- **Node.js** instalado na sua máquina.
- Um **projeto Next.js** criado (ex.: `npx create-next-app`).
- Uma **conta na Discloud** com **subdomínio configurado**.
- Opcionalmente: **Git**, **VSCode** e/ou **CLI da Discloud** para facilitar o fluxo.

Se ainda não tiver familiaridade com o ambiente, confira:

{% content-ref url="../../development-environment/local-environment/nodejs.md" %}
[Ambiente Local Node.js](../../development-environment/local-environment/nodejs.md)
{% endcontent-ref %}

---

## 🧹 Preparando os arquivos do projeto

Antes de compactar seu projeto em `.zip`, crie um arquivo **`.discloudignore`** na raiz do projeto para excluir arquivos e pastas desnecessárias do upload:

```text
node_modules/
dist/
.next/
.env
.env.local
.git
package-lock.json
```

{% hint style="info" %}
O arquivo [`.discloudignore`](../../configurations/.discloudignore.md) funciona de forma semelhante a um `.gitignore`, mas é usado pela Discloud para ignorar arquivos no momento do upload.
{% endhint %}

---

## 📦 `package.json` – scripts recomendados

Dentro do seu `package.json`, garanta que os scripts principais do Next.js estejam definidos. Um exemplo básico:

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "next start -p 8080",
    "export": "next export"
  }
}
```

{% hint style="danger" %}
É importante que o **comando `start` use a porta `8080`** (`next start -p 8080`), pois essa é a porta padrão exigida pela Discloud para websites.
{% endhint %}

---

## ✅ Opção A – Deploy sem servidor custom (Next.js "built-in")

Nesta opção, você usa somente o servidor interno do Next (`next start`), sem precisar de `server.js`.

### 🔁 Fluxo básico

1. Rodar o build localmente (opcional, mas recomendado):
   ```bash
   npm run build
   ```
2. Testar localmente:
   ```bash
   npm run start
   ```
3. Se tudo estiver funcionando, preparar o `.zip` e enviar para a Discloud.

### ⚙️ `discloud.config` (exemplo)

Crie o arquivo `discloud.config` na raiz do projeto com algo similar a:

```text
TYPE=site
BUILD=npm run build
START=npm run start
RAM=512
VERSION=latest
ID=meu-nextjs-app
```

**Campos importantes:**

- `TYPE=site` – indica que é um site/aplicação web.
- `BUILD` – comando executado antes de iniciar a aplicação.
- `START` – comando que inicializa o app (aqui chama `next start -p 8080`).
- `RAM` – quantidade de memória, ajuste conforme seu projeto.

---

## 🧩 Opção B – Custom server com Express

Se você precisa de **rotas customizadas**, **middlewares** ou integrar outras libs antes de delegar ao Next, pode usar um **servidor Express** que usa o Next internamente.

### 🧾 `server.js`

Crie um arquivo `server.js` na raiz do projeto com o seguinte conteúdo:

```js
const express = require("express");
const next = require("next");

const dev = process.env.NODE_ENV !== "production";
const app = next({ dev });
const handle = app.getRequestHandler();

const PORT = process.env.PORT || 8080;

app.prepare().then(() => {
  const server = express();

  server.get("/hello", (req, res) => {
    return res.send("Olá, Discloud!");
  });

  server.all("*", (req, res) => {
    return handle(req, res);
  });

  server.listen(PORT, () => {
    console.log(`Servidor rodando na porta ${PORT}`);
  });
});
```

### 📦 `package.json` (com servidor custom)

Atualize seus scripts para utilizar o `server.js` em produção:

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build",
    "start": "node server.js"
  }
}
```

### ⚙️ `discloud.config` (custom server)

```text
TYPE=site
MAIN=server.js
BUILD=npm run build
START=npm run start
RAM=512
VERSION=latest
ID=meu-nextjs-app-custom-server
```

{% hint style="info" %}
Use esta opção apenas se realmente precisar de um servidor custom. Para a maioria dos projetos, a **Opção A** (sem servidor custom) é mais simples e suficiente.
{% endhint %}

---

## 🧾 Alternativa – Export estático (Next.js como site estático)

Se o seu projeto não depende de **SSR** ou **API Routes**, você pode usar o `next export` para gerar um site totalmente **estático**.

### 📦 `package.json` (export estático)

```json
{
  "scripts": {
    "dev": "next dev",
    "build": "next build && next export",
    "start": "npx serve -s out -l 8080"
  }
}
```

### ⚙️ `discloud.config` (estático)

```text
TYPE=site
BUILD=npm run build
START=npm run start
RAM=256
ID=meu-site-estatico
```

{% hint style="success" %}
Sites estáticos costumam consumir **menos RAM** e são ideais para blogs, landing pages e documentações simples.
{% endhint %}

---

## 🔐 Variáveis de ambiente

No Next.js, variáveis de ambiente públicas devem começar com `NEXT_PUBLIC_`.

- Defina variáveis pelo **Painel da Discloud**, **CLI** ou **API**.
- Tudo que começa com `NEXT_PUBLIC_` é embutido no bundle durante o **build**.

Exemplo:

```env
NEXT_PUBLIC_API_URL=https://meu-backend.discloud.app
API_SECRET_TOKEN=nao-colocar-no-front
```

Usando em componentes:

```js
const apiUrl = process.env.NEXT_PUBLIC_API_URL;
```

{% hint style="danger" %}
Não faça upload de arquivos `.env` no ZIP. Configure as variáveis diretamente na Discloud.
{% endhint %}

---

## 🚀 Fazendo o deploy na Discloud

Você pode fazer deploy do seu app Next.js usando qualquer um dos métodos suportados:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../how-to-host-using/dashboard.md">dashboard.md</a></td><td align="center">Envie o `.zip` pelo Painel da Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../how-to-host-using/discord-bot.md">discord-bot.md</a></td><td align="center">Faça upload usando comandos do bot no Discord.</td><td></td><td></td><td></td></tr><tr><td><a href="../../how-to-host-using/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Envie direto pelo VS Code com a extensão oficial.</td><td></td><td></td><td></td></tr><tr><td><a href="../../how-to-host-using/cli.md">cli.md</a></td><td align="center">Automatize deploys com a CLI da Discloud.</td><td></td><td></td><td></td></tr></tbody></table>

### 📌 Passo a passo via Painel (resumo)

1. **Compacte o projeto** em `.zip` (sem `node_modules`, `.next`, etc.).
2. Acesse o **Painel de Controle** da Discloud.
3. Clique em **Upload** e selecione o `.zip`.
4. Confirme que o `discloud.config` está na raiz e correto.
5. Aguarde o processo de upload e inicialização.
6. Acompanhe os **logs** para verificar se o build e o start foram concluídos com sucesso.

Para mais detalhes, consulte:

{% content-ref url="../../how-to-host-using/dashboard.md" %}
[Painel de Controle](../../how-to-host-using/dashboard.md)
{% endcontent-ref %}

---

## 🗂️ Estrutura final recomendada do projeto

Uma estrutura típica de projeto Next.js para a Discloud pode ser:

```text
my-next-app/
├─ discloud.config
├─ .discloudignore
├─ package.json
├─ next.config.js
├─ server.js        # opcional (apenas na Opção B)
├─ public/
└─ app/ ou pages/
	 ├─ page.js
	 └─ api/
			└─ hello.js
```

---

## 📄 Exemplo completo de `discloud.config`

Para a **Opção A (recomendada)**, um exemplo completo seria:

```text
TYPE=site
BUILD=npm run build
START=npm run start
RAM=512
VERSION=latest
ID=meu-nextjs-app
```

---

## 🛠️ Troubleshooting (erros comuns)

- **Aplicação não abre / porta errada**

  - Verifique se o Next está usando a porta `8080` (`next start -p 8080` ou `PORT=8080`).

- **Erro de plano / permissão**

  - Confirme se sua conta possui o **plano correto** para websites/APIs.

- **Subdomínio não configurado**

  - Certifique-se de ter seguido o guia de **subdomínio** antes do deploy.

- **Erros de build**

  - Execute localmente: `npm run build` e corrija qualquer erro antes de enviar.
  - Confira se todas as **dependências** estão listadas no `package.json`.

- **Erros ao iniciar (`START`)**
  - Verifique se o script `start` está correto.
  - Acompanhe os **logs da Discloud** para ver a mensagem de erro exata.

Para problemas mais específicos, consulte também:

{% content-ref url="../../faq/troubleshooting-solutions/diagnosing-offline-applications.md" %}
[Diagnosticando Aplicações Offline](../../faq/troubleshooting-solutions/diagnosing-offline-applications.md)
{% endcontent-ref %}

---
description: Guia completo para hospedar aplicações JavaScript na Discloud.
icon: square-js
---

# Javascript

## 📁 **Preparando os Arquivos**

Antes de fazer upload do seu projeto, você deve **excluir arquivos desnecessários** para otimizar o deploy.

#### ❌ **Arquivos a Excluir**

Certifique-se de que os seguintes arquivos e diretórios **não** sejam incluídos no seu [`.zip`](../../../faq/perguntas-gerais/em-andamento-como-comprimir.md):

```diff
- package-lock.json
- node_modules/
- .cache/
- .git/
```

📌 **Use um arquivo** [**`.discloudignore`**](../../../configuracoes/.discloudignore.md) **para excluir automaticamente esses arquivos.**

🔗 **Precisa de ajuda para configurar seu** [**`package.json`**](package.json.md) **ou encontrar o** [**arquivo principal**](../../../faq/perguntas-gerais/em-andamento-qual-e-o-arquivo-principal.md)**?**

---

### 🌐 **Hospedando Websites e APIs com Express**

Antes de fazer deploy do seu website ou API na Discloud, certifique-se de que você atenda aos seguintes **requisitos**:

{% hint style="success" %}
[Plano Platinum ou superior](https://discloud.com/plans) é necessário para hospedar websites ou APIs.
{% endhint %}

{% hint style="success" %}
[Um subdomínio deve ser criado](../../../faq/perguntas-gerais/em-andamento-como-criar-um-subdominio.md) antes do deploy.
{% endhint %}

{% hint style="danger" %}
Porta `8080` é obrigatória – As aplicações devem escutar nesta porta.
{% endhint %}

### ⚙️ **Configurando Express**

```javascript
const express = require("express");
const app = express();

app.get("/", (req, res) => {
  res.send("Olá, Discloud!");
});

const PORT = process.env.PORT || 8080;
app.listen(PORT, () => console.log(`Servidor rodando na porta ${PORT}`));
```

{% expand %}

### 📦 Sobre a pasta `dist` (apenas `TYPE=site`)

{% hint style="info" %}
Para aplicações **JavaScript** cujo `TYPE=site` no [`discloud.config`](../../../configuracoes/discloud.config/README.md), a pasta **`dist/` é reservada** para receber o resultado do comando definido em `BUILD`. Você **não precisa (e não deve)** subir arquivos já compilados dentro de `dist/` se optar por deixar a Discloud construir seu projeto.
{% endhint %}

#### ✅ Quando deixar a Discloud buildar
1. Adicione no `discloud.config` a chave `BUILD` com o comando (ex.: `npm run build`).
2. Garanta que seu script de build gere saída em `dist/` (padrão em ferramentas como Vite, Vue CLI, SvelteKit estático, etc.).
3. A plataforma executará o comando antes de iniciar (`START`) e usará o conteúdo de `dist/` automaticamente.

Exemplo (site com Express servindo arquivos estáticos gerados):

```properties
TYPE=site
MAIN=server/index.js
BUILD=npm run build
START=npm run start
RAM=512
VERSION=latest
ID=meusite
```

Scripts típicos em `package.json`:
```json
{
  "scripts": {
    "build": "vite build",
    "start": "node server/index.js"
  }
}
```

#### 👜 Enviando projeto já buildado
Se você prefere fazer o build localmente e **não** quer que a Discloud execute `BUILD`:
* Gere a saída para uma pasta alternativa, por exemplo **`build/`** (para evitar conflito com `dist/`).
* Não defina `BUILD` no `discloud.config`.
* Aponte `MAIN` (e/ou `START`) para dentro dessa pasta.

Exemplo (deploy de saída pré-compilada):
```properties
TYPE=site
MAIN=build/server.js
START=node build/server.js
RAM=512
VERSION=latest
ID=meusite
```

{% endexpand %}

---

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** na Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../como-hospedar-usando/painel-de-controle.md">painel-de-controle.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/bot-do-discord.md">bot-do-discord.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord da Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

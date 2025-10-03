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

***

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

<details>

<summary>📦 Sobre a pasta dist (apenas TYPE=site)</summary>

{% hint style="info" %}
Para apps `TYPE=site`, **`dist/` é reservada** para a saída do `BUILD`. Se você define `BUILD=...` no [`discloud.config`](../../../configuracoes/discloud.config/), nós geramos a pasta `dist/` pra você. **Não compacte `dist/`** ou envie arquivos para lá.
{% endhint %}

{% tabs %}
{% tab title="⚙️ Build automático" %}

1. `BUILD` no `discloud.config` (ex.: `BUILD=npm run build`).
2. Script gera arquivos em `dist/` (Vite, Vue, etc. já fazem isso).
3. Rodamos `BUILD` antes do `START` e servimos `dist/`.

Exemplo:

```properties
TYPE=site
MAIN=server/index.js
BUILD=npm run build
START=npm run start
RAM=512
VERSION=latest
ID=meusite
```

Scripts em `package.json`:

```json
{
  "scripts": {
    "build": "vite build",
    "start": "node server/index.js"
  }
}
```

{% endtab %}

{% tab title="👜 Pré-build" %}

Use se o build é pesado e muda pouco:
* Gere a saída em **`build/`** (não use `dist/`).
* Omitir `BUILD` no `discloud.config`.
* Aponte `MAIN` / `START` para a pasta `build/`.

Exemplo:

```properties
TYPE=site
MAIN=build/server.js
START=node build/server.js
RAM=512
VERSION=latest
ID=meusite
```

{% endtab %}
{% endtabs %}

</details>

***

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** na Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../como-hospedar-usando/painel-de-controle.md">painel-de-controle.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/bot-do-discord.md">bot-do-discord.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord da Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

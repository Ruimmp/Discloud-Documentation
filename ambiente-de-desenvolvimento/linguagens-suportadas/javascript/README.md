---
description: Guia completo para hospedar aplicações JavaScript no Discloud.
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

Antes de fazer deploy do seu website ou API no Discloud, certifique-se de que você atenda aos seguintes **requisitos**:

✔ [Plano Platinum ou superior](https://discloud.com/plans) é necessário para hospedar websites ou APIs.\
✔ [Um subdomínio deve ser criado](../../../faq/perguntas-gerais/em-andamento-como-criar-um-subdominio.md) antes do deploy.\
✔ <mark style="color:red;">Porta</mark> <mark style="color:red;">`8080`</mark> <mark style="color:red;">é</mark> <mark style="color:red;">obrigatória</mark> – As aplicações devem escutar nesta porta.

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

***

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** no Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../como-hospedar-usando/painel-de-controle.md">painel-de-controle.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/bot-do-discord.md">bot-do-discord.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord do Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

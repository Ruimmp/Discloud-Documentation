---
description: Guias completos para hospedar diferentes frameworks e plataformas na Discloud.
icon: window
hidden: true
---

# Frameworks e Plataformas

Cada framework possui suas próprias especialidades, otimizações e configurações específicas. Nesta seção você encontrará guias detalhados para hospedar suas aplicações frontend na Discloud.

## 🚀 Escolha seu Framework

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="nextjs.md">nextjs.md</a></td><td align="center">Full-stack framework com SSR, SSG e renderização estática otimizada para performance.</td><td></td><td></td><td></td></tr><tr><td><a href="react.md">react.md</a></td><td align="center">Biblioteca JavaScript para construir interfaces reativas com bundlers como Vite e Webpack.</td><td></td><td></td><td></td></tr><tr><td><a href="vue-nuxt.md">vue-nuxt.md</a></td><td align="center">Framework reativo com Nuxt para SSR, SSG e aplicações full-stack.</td><td></td><td></td><td></td></tr><tr><td><a href="svelte-astro.md">svelte-astro.md</a></td><td align="center">Frameworks modernos: Svelte para máxima performance e Astro para sites estáticos otimizados.</td><td></td><td></td><td></td></tr><tr><td><a href="static-generators.md">static-generators.md</a></td><td align="center">Geradores estáticos como Hugo, Jekyll e outros para blogs e documentações.</td><td></td><td></td><td></td></tr></tbody></table>

## ⚙️ Configuração Geral

Independente do framework escolhido, todos seguem um padrão geral na Discloud:

### 📋 Requisitos Comuns

- **Arquivo `discloud.config`** configurado corretamente
- **`package.json`** com dependências declaradas (para Node.js)
- **Build script** definido (quando necessário)
- **Porta `8080`** para aplicações que precisam de servidor

### 🔧 Estrutura Típica do `discloud.config`

Para sites e aplicações frontend:

```properties
TYPE=site
MAIN=server.js
BUILD=npm run build
START=npm start
RAM=512
VERSION=latest
ID=meusite
```

**Variáveis importantes:**

- `TYPE=site` → Para aplicações frontend/websites
- `BUILD` → Comando executado antes do start (ex: compilar TypeScript, gerar dist/)
- `START` → Comando para iniciar a aplicação
- `MAIN` → Arquivo principal da aplicação

## 📚 Próximos Passos

1. **Escolha seu framework** nas opções acima
2. **Siga o guia específico** com exemplos e configurações
3. **Configure seu `discloud.config`** conforme recomendações
4. **Faça upload** usando [Dashboard](../how-to-host-using/dashboard.md), [CLI](../how-to-host-using/cli.md), [VSCode](../how-to-host-using/visual-studio-code.md) ou [Discord Bot](../how-to-host-using/discord-bot.md)

## 💡 Dicas Gerais

- Use `.discloudignore` para excluir arquivos desnecessários (node_modules, .cache, etc)
- Sempre teste localmente antes de fazer upload
- Monitore os logs da aplicação para diagnosticar problemas
- Considere aumentar RAM se a aplicação apresentar performance lenta

## ❓ Ainda precisa de ajuda?

Visite a [Seção FAQ](../../faq/general-questions/README.md) ou junte-se ao nosso [Servidor Discord](https://discord.discloudbot.com/) para suporte.

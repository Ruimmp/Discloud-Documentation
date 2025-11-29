---
description: Guias completos para hospedar diferentes frameworks na Discloud.
icon: window
---

# Frameworks

## 🎯 Visão geral

Guias para fazer deploy de seus frameworks favoritos na Discloud. Cada um cobre o que você precisa fazer localmente e como colocar rodando na plataforma.

Seja uma API simples, uma app completa ou algo em tempo real – você vai encontrar passos adaptados para seu framework.

---

## 📚 Guias disponíveis

Escolha seu framework da lista e acompanhe:

- **Setup passo a passo** – Estrutura do projeto, arquivos de config, variáveis de ambiente
- **Testes locais** – Como verificar se tudo funciona antes de enviar
- **Deploy** – Coloque seu app online e acessível
- **Troubleshooting** – Problemas comuns e como resolver

---

## 🚀 O básico

1. Escolha seu framework
2. Siga o guia para configurar localmente
3. Teste o build para produção
4. Faça deploy na Discloud

---

## 💡 O que é obrigatório

Não importa qual framework você use:

- **Porta 8080** – Seu app escuta aqui. É assim que o tráfego é roteado.
- **Subdomínio** – [Crie um seguindo este guia](../../faq/general-questions/how-to-create-a-subdomain.md).
- **`discloud.config`** – Fica na raiz do projeto. [Veja o guia de config](../../configurations/discloud.config/README.md).
- **Arquivo de dependências** – `package.json`, `requirements.txt`, o que seu framework usar.

---

## 🔗 Links úteis

- 📖 [Ambiente de desenvolvimento](../../development-environment/supported-languages/README.md) – Configure Node, Python, etc. localmente
- ⚙️ [discloud.config](../../configurations/discloud.config/README.md) – Todas as opções de config
- 🚀 [Como fazer deploy](../../how-to-host-using/dashboard.md) – Dashboard, Bot, CLI ou VSCode
- 🌐 [Domínios customizados](../../api-and-integrations/custom-domain.md) – Use seu próprio domínio

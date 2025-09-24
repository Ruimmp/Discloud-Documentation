---
description: Guia completo para hospedar aplicações Rust no Discloud.
icon: rust
---

# Rust

## 📁 **Preparando os Arquivos**

Antes de fazer upload do seu projeto, você deve **excluir arquivos desnecessários** para otimizar o deploy.

#### ❌ **Arquivos a Excluir**

Certifique-se de que os seguintes arquivos e diretórios **não** sejam incluídos no seu [`.zip`](../../../faq/general-questions/wip-how-to-compress.md):

```diff
- Cargo.lock
- target/
- git
```

📌 **Use um arquivo** [**`.discloudignore`**](../../../configurations/.discloudignore.md) **para excluir automaticamente esses arquivos.**

🔗 **Precisa de ajuda para configurar seu** [**`Cargo.toml`**](cargo.toml.md) **ou encontrar o** [**arquivo principal**](../../../faq/general-questions/wip-what-is-the-main-file.md)**?**

---

## 🌐 Hospedando Seu Site com Rocket

Antes de fazer deploy do seu website ou API no Discloud, certifique-se de que você atenda aos seguintes **requisitos**:

✔ [Plano Platinum ou superior](https://discloud.com/plans) é necessário para hospedar websites ou APIs.\
✔ [Um subdomínio deve ser criado](../../../faq/general-questions/wip-how-to-create-a-subdomain.md) antes do deploy.\
✔ <mark style="color:red;">Porta</mark> <mark style="color:red;"></mark><mark style="color:red;">`8080`</mark> <mark style="color:red;"></mark><mark style="color:red;">é</mark> <mark style="color:red;">obrigatória</mark> – As aplicações devem escutar nesta porta.\
✔ Use a versão nightly do Rust (Rocket requer nightly).

---

## 🚀 Configurando `Rocket`

[Rocket](https://rocket.rs/) é um framework web para Rust que requer a versão nightly do Rust. Para configurar e fazer deploy de um projeto Rocket no Discloud, siga estes passos:

{% stepper %}
{% step %}
Defina a Versão Nightly do Rust.

Execute o seguinte comando no terminal para garantir que seu projeto esteja usando a versão nightly:

```bash
rustup override set nightly
```

{% endstep %}

{% step %}
Crie o Arquivo `rust-toolchain.toml`.

Para garantir que a versão nightly do Rust seja usada, crie um arquivo chamado `rust-toolchain.toml` no diretório raiz do projeto com o seguinte conteúdo:

{% code title="rust-toolchain.toml" %}

```ini
[toolchain]
channel = "nightly"
```

{% endcode %}

Este arquivo informa ao rustup para usar a versão nightly do Rust.
{% endstep %}
{% endstepper %}

---

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** no Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../how-to-host-using/dashboard.md">dashboard.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../how-to-host-using/discord-bot.md">discord-bot.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord do Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../how-to-host-using/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../how-to-host-using/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

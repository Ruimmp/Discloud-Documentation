---
description: Aprenda a hospedar seu bot em JavaScript na DisCloud
---

# 📄 Criar o Cargo.toml

O arquivo `Cargo.toml` é um arquivo manifesto do **gerenciador de pacotes cargo**. Este arquivo contém metadados como **nome**, **versão** e **dependências** para pacotes, que são chamados de "[crates](https://crates.io/)" em **Rust**.

### Como criar o arquivo `Cargo.toml`?

#### Começando um novo [package](https://doc.rust-lang.org/cargo/appendix/glossary.html#package) com Cargo num diretório existente

Abra o Terminal no diretório do seu projeto e execute:

```shell
cargo init
```

> Se preferir que o Cargo crie o diretório automaticamente use `cargo new botrs`

{% hint style="info" %}
Modifique **botrs** para o nome do seu projeto seguindo a estrutura **snake\_case** ou **kebab-case**
{% endhint %}

![](../../../.gitbook/assets/cargo\_init.png)

{% hint style="info" %}
Você precisa do **Rust e Cargo** instalado no seu computador, caso não esteja instalado siga as instruções abaixo.
{% endhint %}

{% content-ref url="../../../ambiente-local/instalar/rust.md" %}
[rust.md](../../../ambiente-local/instalar/rust.md)
{% endcontent-ref %}

### Colocando dependências no seu `Cargo.toml`

#### instalando o [serenity](https://github.com/serenity-rs/serenity)

> **Serenity** - é uma biblioteca Rust para usar a API do Discord

Adicione a seguinte linha no seu arquivo`Cargo.toml` ou execute `cargo add serenity`

{% code title="Cargo.toml" %}
```toml
[dependencies]
serenity = "0.11"
```
{% endcode %}

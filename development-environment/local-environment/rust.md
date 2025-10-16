---
description: >-
  Instale Rust usando rustup, gerencie toolchains e verifique cargo para
  desenvolvimento local antes de fazer o upload na Discloud.
icon: rust
---

# Rust

## 🧾 Visão Geral

Rust fornece performance, segurança de memória e uso previsível de recursos para APIs, workers e bots. Instale com `rustup` para gerenciar toolchains localmente antes de fazer o upload.

***

## 📥 Instalação (escolha seu SO)

{% tabs %}
{% tab title="🪟 Windows" %}
{% tabs %}
{% tab title="rustup-init (Oficial)" %}
{% stepper %}
{% step %}
Baixe o instalador: https://win.rustup.rs/ (ou execute o comando abaixo no PowerShell)
{% endstep %}

{% step %}
Execute e aceite os padrões (instala no perfil do usuário).
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="Alternativo (PowerShell):" %}
```bash
irm https://win.rustup.rs -UseBasicParsing | iex
```
{% endtab %}
{% endtabs %}

**Verificar**

```bash
rustc --version
cargo --version
```

**Atualizar Toolchain**

```bash
rustup update
```
{% endtab %}

{% tab title="🐧 Linux" %}
Instale via script rustup:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
rustc --version
cargo --version
```

**Adicionar Build Essentials (Debian/Ubuntu)**

```bash
sudo apt update
sudo apt install -y build-essential pkg-config libssl-dev
```

**Atualizar**

```bash
rustup update
```

**Remover Toolchain**

```bash
rustup self uninstall
```
{% endtab %}

{% tab title="🍎 macOS" %}
Instale com rustup:

```bash
curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
source ~/.cargo/env
rustc --version
cargo --version
```

Adicionar ferramentas de build (se não presentes):

```bash
xcode-select --install  # solicita ferramentas de desenvolvedor
```

Atualizar:

```bash
rustup update
```
{% endtab %}
{% endtabs %}

***

## 🧰 Toolchains e Componentes

{% stepper %}
{% step %}
Listar instalados

```bash
rustup toolchain list
```
{% endstep %}

{% step %}
Adicionar nightly (opcional)

```bash
rustup toolchain install nightly
```
{% endstep %}

{% step %}
Definir padrão

```bash
rustup default stable
```
{% endstep %}

{% step %}
Adicionar componentes (exemplo)

```bash
rustup component add clippy rustfmt
```
{% endstep %}
{% endstepper %}

***

## 🗂 Inicialização do Projeto

Criar novo projeto:

```bash
cargo new myapp
cd myapp
cargo build
```

Executar:

```bash
cargo run
```

Formatar e lintar:

```bash
cargo fmt -- --check
cargo clippy -- -D warnings
```

***

## 🗃 Comandos Cargo Comuns

```bash
cargo new api-service          # criar projeto binário
cargo build --release          # build otimizado
cargo run                      # build + executar
cargo test                     # executar testes
cargo update                   # atualizar lock de dependências
cargo tree                     # gráfico de dependências (requer cargo-tree)
cargo doc --open               # construir docs localmente
```

Instalar cargo tree (se faltar):

```bash
cargo install cargo-tree
```

***

## 📦 Gerenciamento de Dependências

Dependências declaradas em [`Cargo.toml`](../supported-languages/rust/cargo.toml.md) sob `[dependencies]`:

```toml
[dependencies]
reqwest = { version = "0.12", features = ["json"] }
serde = { version = "1", features = ["derive"] }
tokio = { version = "1", features = ["rt-multi-thread", "macros"] }
```

Atualizar lockfile:

```bash
cargo update
```

***

## 🔄 Atualização

```bash
rustup update            # atualizar todas as toolchains
rustup self update       # atualizar rustup em si
```

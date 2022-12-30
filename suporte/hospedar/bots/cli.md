---
description: Hospede e gerencie a sua aplicação sem sair do seu VSCode!
---

# ⌨ DisCloud CLI

Um **CLI (Command-line interface)** é um programa baseado em comandos de texto.

## :pencil: Requisitos

#### 1. Você precisa de usar o comando [**api**](../../comandos/api.md)**, para obter o seu token da API da DisCloud**.

<figure><img src="../../../.gitbook/assets/api-cmd.png" alt=""><figcaption><p>Usando o comando .api</p></figcaption></figure>

## :keyboard: DisCloud CLI

A DisCloud mantém oficialmente **2 projetos CLI** em **2 linguagens diferentes**, use a que for mais conveniente.

{% tabs %}
{% tab title="🟨JavaScript" %}
## 1. Download

> Necessita do [NodeJS](../../../ambiente-local/instalar/javascript.md) instalado

### Windows / Linux

```shell
npm i -g discloud-cli
```

## 2. Reabra o Terminal

## 3. Verifique a Instalação

```shell
discloud --version
```

{% hint style="success" %}
Se aparecer a versão, significa que foi instalado corretamente
{% endhint %}

## 4.  Fazer Login

```
discloud login
```

[Link para o repositório do projeto](https://github.com/discloud/cli)
{% endtab %}

{% tab title="🦀Rust (NEW)" %}
## 1. Download do Instalador

### Windows

```powershell
. {iwr -useb "https://discloud.github.io/cli-rust/installer/windows.ps1"} | iex;
```

### Linux

```shell
curl -L https://discloud.github.io/cli-rust/installer/linux | bash
```

## 2. Reabra o seu Terminal

## 3. Verifique a instalação

```
discloud --version
```

{% hint style="success" %}
Se aparecer a versão, significa que foi instalado corretamente
{% endhint %}

## 4. Fazer Login

```shell
discloud login TOKEN_AQUI
```

[Link para o repositório do projeto](https://github.com/discloud/cli-rust)
{% endtab %}
{% endtabs %}

## :thumbsup: Dicas e Truques

### Init

Use o comando `discloud init` para criar o seu **discloud.config** de uma forma fácil, intuitiva, e rápida!


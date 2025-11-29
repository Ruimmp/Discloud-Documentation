---
description: >-
  Aprenda como instalar, configurar e começar a usar a biblioteca NPM
  discloud.app para gerenciar sua aplicação Discloud.
icon: flag-checkered
---

# Introdução

## 📦 Instalação

Você pode instalar a biblioteca **discloud.app** usando seu gerenciador de pacotes preferido:

{% tabs %}
{% tab title="NPM" %}
```bash
npm install discloud.app
```
{% endtab %}

{% tab title="Yarn" %}
```bash
yarn add discloud.app
```
{% endtab %}

{% tab title="PNPM" %}
```bash
pnpm add discloud.app
```
{% endtab %}

{% tab title="Bun" %}
```bash
bun add discloud.app
```
{% endtab %}
{% endtabs %}

## 🔑 Obtendo Seu Token da API

Antes de usar a biblioteca, você precisa obter seu **Token da API da Discloud**.

Para instruções detalhadas sobre como obter seu token da API, veja [aqui](../../faq/general-questions/how-can-i-get-my-discloud-api-token.md).

{% hint style="warning" %}
**Mantenha seu token seguro!** Nunca o compartilhe publicamente ou faça commit dele no controle de versão. Armazene-o em variáveis de ambiente ou arquivos de configuração seguros.
{% endhint %}

## 🚀 Configuração Básica

### Configuração de Variáveis de Ambiente

{% stepper %}
{% step %}
Crie um arquivo `.env` na raiz do seu projeto para armazenar seu token da API com segurança:

{% code title=".env" %}
```bash
DISCLOUD_TOKEN=your_api_token_here
```
{% endcode %}
{% endstep %}

{% step %}
Instale o pacote **dotenv** para carregar variáveis de ambiente:

```bash
npm install dotenv
```
{% endstep %}

{% step %}
Então use-o em sua aplicação:

{% code title="index.js" %}
```javascript
require("dotenv").config(); // Carregar variáveis de ambiente
const { discloud } = require("discloud.app");

async function main() {
  try {
    // Autenticar usando variável de ambiente
    await discloud.login(process.env.DISCLOUD_TOKEN);
    console.log("Autenticação bem-sucedida com Discloud!");

    // Sua lógica de aplicação aqui...
  } catch (error) {
    console.error("Falha na autenticação:", error.message);
  }
}

main();
```
{% endcode %}
{% endstep %}
{% endstepper %}

## 🎯 Sua Primeira Chamada da API

Vamos testar a conexão buscando informações sobre suas aplicações:

{% code title="test-connection.js" %}
```javascript
require("dotenv").config(); // Carregar variáveis de ambiente
const { discloud } = require("discloud.app");

async function testConnection() {
  try {
    // Autenticar
    await discloud.login(process.env.DISCLOUD_TOKEN);

    // Buscar todas as suas aplicações
    const apps = await discloud.apps.fetch("all");

    console.log(`Encontradas ${apps.size} aplicações:`);
    apps.forEach((app, id) => {
      console.log(`- ${app.name} (ID: ${id})`);
    });
  } catch (error) {
    console.error("Erro:", error.message);
  }
}

testConnection();
```
{% endcode %}

## 📁 Suporte ao TypeScript

A biblioteca inclui suporte completo ao **TypeScript** com definições de tipo:

{% code title="index.ts" %}
```typescript
import "dotenv/config"; // Carregar variáveis de ambiente
import { discloud, App } from "discloud.app";

async function main(): Promise<void> {
  try {
    await discloud.login(process.env.DISCLOUD_TOKEN!);

    // Buscar uma aplicação específica com suporte completo de tipos
    const app: App = await discloud.apps.fetch("your_app_id");

    console.log(`App: ${app.name}`);
    console.log(`Status: ${app.online ? "Online" : "Offline"}`);
    console.log(`RAM: ${app.ram}MB`);
  } catch (error) {
    console.error("Erro:", error);
  }
}

main();
```
{% endcode %}

***

{% hint style="success" %}
**Pronto para começar!** Você configurou com sucesso a biblioteca discloud.app. Confira [Exemplos de Uso](usage-examples.md) para ver o que você pode construir!
{% endhint %}

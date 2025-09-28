---
description: >-
  Aprenda a hospedar suas aplicações de forma rápida e fácil usando uma de
  nossas CLIs.
icon: terminal
---

# CLI

A **Discloud CLI** permite que você **hospede e gerencie suas aplicações** diretamente da linha de comando, fornecendo uma maneira rápida e eficiente de interagir com seu app.

***

## 🔑 **Política de Execução do Windows (Apenas para Usuários do Windows)**

### 🛠️ O que é Política de Execução? <a href="#o-que-e-politica-de-execucao" id="o-que-e-politica-de-execucao"></a>

A Política de Execução protege seu sistema limitando a execução de scripts não assinados. O modo **RemoteSigned** permite que scripts locais sejam executados sem assinaturas, mas requer uma assinatura para scripts baixados da internet.

### ❓ **Como Habilitar a Execução de Scripts**

{% stepper %}
{% step %}
Abra o PowerShell como Administrador.
{% endstep %}

{% step %}
Execute o seguinte comando.

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
{% endstep %}

{% step %}
Confirme a alteração digitando `Y` e pressionando Enter.
{% endstep %}

{% step %}
Reinicie o PowerShell e tente executar os comandos da Discloud CLI novamente.
{% endstep %}
{% endstepper %}

***

## 🔧 Instalando a Discloud CLI

{% tabs %}
{% tab title="📦 Node.js" %}
{% stepper %}
{% step %}
Pré-requisito.

Certifique-se de que você tenha [NodeJS](../ambiente-de-desenvolvimento/ambiente-local/nodejs.md) instalado em seu sistema.
{% endstep %}

{% step %}
Instale a CLI.

```bash
npm install -g discloud.app
```
{% endstep %}

{% step %}
**Reabra o terminal** para aplicar as alterações.
{% endstep %}

{% step %}
Verifique a Instalação.

Após a instalação, execute o seguinte comando para verificar se a CLI foi instalada corretamente:

```bash
discloud --version
```

{% hint style="success" %}
Se a versão da CLI for exibida, a instalação foi bem-sucedida.
{% endhint %}

{% hint style="info" %}
**Atualização da CLI**

Para atualizar a CLI, execute o seguinte comando:

```bash
npm update -g discloud-cli
```
{% endhint %}
{% endstep %}

{% step %}
Login.

Para acessar as funcionalidades da CLI, você precisa fazer login com suas credenciais da Discloud. Execute o seguinte comando e cole seu [Token da API Discloud](../faq/perguntas-gerais/como-obter-o-meu-token-da-api-da-discloud.md):

```bash
discloud --login
```
{% endstep %}
{% endstepper %}

{% hint style="info" %}
**Repositório Oficial da CLI**

A CLI do NodeJS é um projeto de código aberto. Você pode contribuir, relatar bugs e sugerir melhorias no repositório oficial.

{% embed url="https://github.com/discloud/cli" %}
{% endhint %}
{% endtab %}
{% endtabs %}

***

## 🚀 Fazendo Upload da Sua Aplicação

Uma vez instalada e configurada, você pode **fazer o upload da sua aplicação** em apenas algumas etapas.

{% stepper %}
{% step %}
Preparando seu projeto.

* Certifique-se de que seu projeto contenha todos os arquivos necessários:
  * [**`discloud.config`**](https://github.com/discloud/docs/blob/portuguese-revamp/configuracoes/discloud.config) (arquivo de configuração).
  * **Dependências necessárias** para sua linguagem de programação (ex.: [`package.json`](../ambiente-de-desenvolvimento/linguagens-suportadas/javascript/package.json.md) para [Node.js](../ambiente-de-desenvolvimento/ambiente-local/nodejs.md), [`requirements.txt`](../ambiente-de-desenvolvimento/linguagens-suportadas/python/requirements.txt.md) para [Python](../ambiente-de-desenvolvimento/ambiente-local/python.md)).
* **Verifique o** [**Guia de Linguagens**](../ambiente-de-desenvolvimento/linguagens-suportadas/) para garantir que seu projeto esteja estruturado corretamente.
{% endstep %}

{% step %}
Fazendo upload de sua aplicação.

Para fazer o upload do seu projeto, navegue até a pasta da sua aplicação e execute:

```bash
discloud up
```

* A CLI irá **automaticamente comprimir** seu projeto e fazer upload dele.
* Uma vez concluído, sua aplicação irá **começar a funcionar** na Discloud.

{% hint style="info" %}
**Para verificar o status do seu app, use:**

```sh
discloud status
```
{% endhint %}
{% endstep %}
{% endstepper %}

***

## 📌 Dicas e Truques

### ✨ **Usando `discloud init` para Gerar Configuração Automaticamente**

Em vez de criar manualmente o arquivo **`discloud.config`**, você pode gerá-lo automaticamente usando:

```sh
discloud init
```

* Este comando solicita que você insira **detalhes básicos de configuração** (ex.: nome, arquivo principal, RAM, etc.).
* Em seguida, **gera o arquivo** [**`discloud.config`**](https://github.com/discloud/docs/blob/portuguese-revamp/configuracoes/discloud.config) **para você**, facilitando o upload.

### 📂 **Usando `.discloudignore` para Excluir Arquivos**

Se você quiser **excluir certos arquivos ou diretórios** do upload, você pode criar um arquivo [`.discloudignore`](../configuracoes/.discloudignore.md) na raiz do seu projeto.

***

## **❓ Ainda precisa de ajuda?**

Verifique a [**Seção FAQ**](https://github.com/discloud/docs/blob/portuguese-revamp/como-hospedar-usando/broken-reference/README.md) ou junte-se ao nosso [**Servidor Discord**](https://discord.discloudbot.com/) para suporte.

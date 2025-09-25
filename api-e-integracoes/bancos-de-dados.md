---
description: >-
  Visão geral das opções de banco de dados para apps Discloud, templates
  integrados (MySQL, PostgreSQL, Redis, MongoDB) e configuração externa do
  MongoDB Atlas.
icon: database
---

# Bancos de Dados

## 🧭 Visão Geral

Aplicações Discloud podem se conectar a:

* [Templates de serviço gerenciado integrados que você provisiona através do catálogo de Templates.](bancos-de-dados.md#template-catalog-managed-instances)
* [Provedor de banco de dados como serviço MongoDB Atlas externo que você configura manualmente.](bancos-de-dados.md#using-external-mongodb-atlas)

***

## 📦 Catálogo de Templates (Instâncias Gerenciadas)

Provisionando um template de banco de dados (ex. MySQL, PostgreSQL, Redis, MongoDB):

{% stepper %}
{% step %}
Abra a página de Templates: [https://discloud.com/templates](https://discloud.com/templates)
{% endstep %}

{% step %}
Escolha o template desejado (motor de banco de dados ou painel de ferramentas).
{% endstep %}

{% step %}
Forneça um nome e variáveis de ambiente necessárias (a UI indica as obrigatórias).
{% endstep %}

{% step %}
Implante. Credenciais / strings de conexão ficam disponíveis para a configuração do seu app.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
**📨 Precisa de Outro Template?**

Abra um [ticket de suporte](https://discord.com/channels/@me/930852077045940224/) no [servidor Discord](https://discord.discloudbot.com/) com o nome do motor, versão e caso de uso. A equipe avalia a viabilidade e pode adicioná-lo ao catálogo.
{% endhint %}

***

## 🌍 Usando MongoDB Atlas Externo

Se você optar pelo MongoDB Atlas em vez de um template:

{% stepper %}
{% step %}
Crie um cluster gratuito ou pago em [https://www.mongodb.com/](https://www.mongodb.com/)
{% endstep %}

{% step %}
Em Network Access, adicione IP: `0.0.0.0/0` (Permitir de Qualquer Lugar) para que os contêineres Discloud possam se conectar.
{% endstep %}

{% step %}
Teste a conectividade localmente antes de implantar, se possível.
{% endstep %}
{% endstepper %}

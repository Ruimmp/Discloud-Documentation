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

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="databases.md#catalogo-de-templates-instancias-gerenciadas">#catalogo-de-templates-instancias-gerenciadas</a></td><td>Templates de serviço gerenciado integrados que você provisiona através do catálogo de Templates.</td><td></td><td></td><td></td></tr><tr><td><a href="databases.md#usando-mongodb-atlas-externo">#usando-mongodb-atlas-externo</a></td><td>Provedor de banco de dados como serviço MongoDB Atlas externo que você configura manualmente.</td><td></td><td></td><td></td></tr></tbody></table>

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
Hospede. Credenciais / strings de conexão ficam disponíveis para a configuração do seu app.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
#### **Precisa de Outro Template?**

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
Teste a conectividade localmente antes de fazer o upload, se possível.
{% endstep %}
{% endstepper %}

{% tabs %}
{% tab title="Vídeo explicativo recomendado" %}
{% embed url="https://youtu.be/kGPY9ZuJ0b0" %}
{% endtab %}
{% endtabs %}

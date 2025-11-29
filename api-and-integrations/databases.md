---
description: >-
  Overview of database options for Discloud apps, built-in templates (MySQL,
  PostgreSQL, Redis, MongoDB) and external MongoDB Atlas configuration.
icon: database
---

# Databases

## 🧭 Overview

Discloud applications can connect either to:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="databases.md#template-catalog-managed-instances">#template-catalog-managed-instances</a></td><td>Built-in managed service templates you provision through the Templates catalog.</td><td></td><td></td><td></td></tr><tr><td><a href="databases.md#using-external-mongodb-atlas">#using-external-mongodb-atlas</a></td><td>External MongoDB Atlas database-as-a-Service provider that you configure manually.</td><td></td><td></td><td></td></tr></tbody></table>

***

## 📦 Template Catalog (Managed Instances)

Provisioning a database template (e.g. MySQL, PostgreSQL, Redis, MongoDB):

{% stepper %}
{% step %}
Open the Templates page: [https://discloud.com/templates](https://discloud.com/templates)
{% endstep %}

{% step %}
Choose the desired template (database engine or tooling panel).
{% endstep %}

{% step %}
Provide a name and required environment variables (the UI indicates mandatory ones).
{% endstep %}

{% step %}
Deploy. Credentials / connection strings become available for your app configuration.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
#### **Need Another Template?**

Open a [support ticket](https://discord.com/channels/@me/930852077045940224/) in the [Discord server](https://discord.discloudbot.com/) with the engine name, version, and use case. The team evaluates feasibility and may add it to the catalog.
{% endhint %}

***

## 🌍 Using External MongoDB Atlas

If you opt for MongoDB Atlas instead of a template:

{% stepper %}
{% step %}
Create a free or paid cluster at [https://www.mongodb.com/](https://www.mongodb.com/)
{% endstep %}

{% step %}
In Network Access, add IP: `0.0.0.0/0` (Allow from Anywhere) so Discloud containers can connect.
{% endstep %}

{% step %}
Test connectivity locally before deploying if possible.
{% endstep %}
{% endstepper %}

{% tabs %}
{% tab title="Recommended video walkthrough" %}
{% embed url="https://youtu.be/kGPY9ZuJ0b0" %}
{% endtab %}
{% endtabs %}

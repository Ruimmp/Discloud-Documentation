---
description: >-
  Overview of database options for Discloud apps, built-in templates (MySQL,
  PostgreSQL, Redis, MongoDB) and external MongoDB Atlas configuration.
icon: database
---

# Databases

## 🧭 Overview

Discloud applications can connect either to:

* [Built-in managed service templates you provision through the Templates catalog.](databases.md#template-catalog-managed-instances)
* [External MongoDB Atlas database-as-a-Service provider that you configure manually.](databases.md#using-external-mongodb-atlas)

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
#### 📨 Need Another Template?

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

---
description: Deploy apps from GitHub to Discloud in 3 steps.
icon: github
---

# GitHub Integration

## ✅ **Prerequisites**

{% stepper %}
{% step %}
**GitHub Account Consistency**

{% hint style="warning" %}
The GitHub account used for **Discloud login** AND **Repository ownership, must be the same.**
{% endhint %}

> **Consequences of mismatch**:
>
> * Repositories won't appear
> * Deployment failures
> * Permission errors
{% endstep %}

{% step %}
**Valid** [**`discloud.config`**](../configurations/discloud.config/) **File**

Must exist in your repository's **root directory.**

> ⚠️ **Validation fails if**:
>
> * File missing
> * Invalid syntax
{% endstep %}
{% endstepper %}

***

## 🔄 **Connect GitHub & Configure Access**

{% stepper %}
{% step %}
**Initiate GitHub Connection**

* Go to [Discloud Dashboard](https://discloud.com/dashboard) → **GitHub Integration** tab
*   Click **Login** → Authorize Discloud via GitHub OAuth

    <figure><img src="../.gitbook/assets/GitHub-Integration_Login.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
**Configure Repository Access**

* Return to **GitHub Integration** → Click **Configure**
* Choose installation target.
* Set permissions:
  * 🔓 _All repositories_
  * 🔒 _Select specific repositories_
{% endstep %}
{% endstepper %}

***

## 🚀 **Deploy from GitHub**

{% stepper %}
{% step %}
**Start Deployment**

* Go to [Discloud Dashboard](https://discloud.com/dashboard)
* Click "**+ Upload"** (top-right corner)
* Select "**GitHub"** from the menu
{% endstep %}

{% step %}
#### **Configuration & Upload**

{% hint style="info" %}
#### 🔐 Secure Environment Variables

Use [`.env`](../faq/general-questions/wip-.env-file.md) files locally for development, but ensure they're added to `.gitignore` to prevent accidental exposure on GitHub. When deploying via Discloud's GitHub integration, **add production secrets directly in the "Environment Variables" section** during configuration.
{% endhint %}
{% endstep %}
{% endstepper %}

<figure><img src="../.gitbook/assets/GitHub-Integration_Upload.gif" alt=""><figcaption></figcaption></figure>

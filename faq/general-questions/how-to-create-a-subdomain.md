---
description: Learn how to register and manage custom Discloud subdomains for your applications.
---

# How to Create a Subdomain?

## 🌐 What is a Discloud Subdomain?

On **Discloud**, any app that uses a **port** and requires **external access** through it to be accessed is considered a site. This includes bots with dashboards, dashboards, APIs, static and dynamic sites, and many others…

To allow external access to your app, Discloud offers the option to create a **custom subdomain**. This subdomain redirects traffic through the Discloud proxy to **port 8080** of your app, allowing you and users to access your site **securely and reliably**.

### 📡 How it Works

<figure>
  <img src="../../.gitbook/assets/subdomain-flow.png" alt="Discloud subdomain flow">
  <figcaption></figcaption>
</figure>

---

## ✅ Requirements

To register and use a Discloud subdomain, you must meet the following requirements:

{% hint style="success" %}
[Platinum Plan or Higher](https://discloud.com/plans) is required to host websites or APIs.
{% endhint %}

{% hint style="success" %}
**Port 8080** – Your application must listen on port 8080 for external traffic
{% endhint %}

{% hint style="success" %}
**Discloud Config** – Your app must include a properly configured [`discloud.config`](../../configurations/discloud.config/) file
{% endhint %}

---

## 🚀 Register Your Subdomain

### Via Dashboard

{% stepper %}
{% step %}
Open the [**Discloud Dashboard**](https://discloud.com/dashboard).
{% endstep %}

{% step %}
Click on the `Subdomain` tab at the top of the application page.

<figure>
  <img src="../../.gitbook/assets/dashboard-subdomain-tab.png" alt="Dashboard Subdomain tab">
  <figcaption></figcaption>
</figure>
{% endstep %}

{% step %}
Click the `+ Subdomain` button to create a new subdomain.

<figure>
  <img src="../../.gitbook/assets/dashboard-subdomain-button.png" alt="Add Subdomain button">
  <figcaption></figcaption>
</figure>
{% endstep %}

{% step %}
Enter your desired subdomain name (e.g., `myapp`, `dashboard`, `api`).

{% hint style="info" %}
**Subdomain naming rules:**
- Maximum **20 characters**
- Only alphanumeric characters (A–Z, 0–9) and hyphens (-)
- No spaces, underscores, or special characters allowed
- Example: ✅ `my-app-v1` | ❌ `my_app_v1` | ❌ `my app`
{% endhint %}
{% endstep %}

{% step %}
Click **Create** and wait for confirmation. Your subdomain is now registered and its state will show as **Available**.

<figure>
  <img src="../../.gitbook/assets/dashboard-subdomain-available.png" alt="Subdomain registered and available">
  <figcaption></figcaption>
</figure>
{% endstep %}

{% endstepper %}

{% endstepper %}

---

## 📝 Configure Your discloud.config

Once your subdomain is registered, you **must** add it to your `discloud.config` file so Discloud routes traffic to the correct app.

Open your `discloud.config` file and locate the `ID` field:

```ini
ID=your-subdomain-name
```

{% hint style="warning" %}
**Important:** Use only the subdomain name, **not** the full domain (e.g., use `myapp`, not `myapp.discloud.app`).

{% code title="discloud.config" %}

Example configuration:

```ini
TYPE=site
MAIN=index.js
RAM=256
ID=myapp
APT=nginx
```

{% endcode %}

{% endhint %}

After updating `discloud.config`, **deploy your application** for the changes to take effect.

{% content-ref url="../../configurations/discloud.config/" %}
[discloud.config](../../configurations/discloud.config/)
{% endcontent-ref %}

---

## 🔄 Subdomain States

Your registered subdomain can have two states:

| State            | Description                                                                                                                                                                    |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| 🟢 **Available** | The subdomain is **registered and available**. No app is currently using it (no active deployment). You can deploy an app to activate it at any time.                          |
| 🔵 **Active**    | The subdomain is **registered and in use**. An app is currently deployed and accessible at `https://subdomain.discloud.app`. Traffic is being routed to your app on port 8080. |

---

## 🌍 Access Your Site

Once your subdomain is **Active**, you can access it via:

```
https://your-subdomain-name.discloud.app
```

---

## ⚙️ Advanced: Custom Domain

If you want to use your own domain (e.g., `myapp.com`) instead of a Discloud subdomain, check out our [**Custom Domain Guide**](../../api-and-integrations/custom-domain.md).

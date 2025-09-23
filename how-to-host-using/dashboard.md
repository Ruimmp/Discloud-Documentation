---
description: Learn how to quickly and easily host your application using the Dashboard.
icon: table-columns
---

# Dashboard

## 📁 Preparing Your Project Files

Before uploading your project, ensure that your **files are correctly structured** according to the programming language you're using. Different languages have specific requirements for dependency management, project structure, and necessary files.

{% content-ref url="../development-environment/supported-languages/" %}
[supported-languages](../development-environment/supported-languages/)
{% endcontent-ref %}

### 📌 **Basic Requirements**

* **Project Source Code** – All the necessary files for your application to run.
* **Configuration File (**[**`discloud.config`**](../configurations/discloud.config/)**)** – Required for deployment settings.
* **Dependencies File** (if applicable):
  * [`package.json`](../development-environment/supported-languages/javascript/package.json.md) for [**Node.js**](../development-environment/local-environment/nodejs.md)
  * [`requirements.txt`](../development-environment/supported-languages/python/requirements.txt.md) for [**Python**](../development-environment/local-environment/python.md)
  * [`Cargo.toml`](../development-environment/supported-languages/rust/cargo.toml.md) for [**Rust**](../development-environment/local-environment/rust.md)
  * [`Gemfile`](../development-environment/supported-languages/ruby/gemfile.md) for [**Ruby**](../development-environment/local-environment/ruby.md)

### **🗑️** Excluding Unnecessary Files

To **optimize your deployment**, make sure to **remove unnecessary files** before compressing your project into a `.zip` file.

#### ❌ Common files and folders to exclude:

```diff
- node_modules
- venv
- .git
- .DS_Store
- __pycache__
```

> For detailed information on required files and appropriate configurations, refer to the [**documentation of the language**](../development-environment/supported-languages/) you are using for your project.

***

## 🔑 Authentication – Logging into your Dashboard

Before deploying your app, you need to **log into Discloud**:

{% stepper %}
{% step %}
Visit the [Discloud](https://discloud.com/).
{% endstep %}

{% step %}
Click **"Enter"** and log in.

<details>

<summary>Access the <strong>Dashboard</strong> if you are already logged in.</summary>

![](../.gitbook/assets/Website-Access_Dashboard.png)

</details>

<figure><img src="../.gitbook/assets/Website-Sign_In.png" alt=""><figcaption></figcaption></figure>
{% endstep %}
{% endstepper %}

***

## 🚀 Uploading Your Application

Once your files are ready, follow these steps to upload and deploy your app.

{% stepper %}
{% step %}
Compressing Your Project.

Before uploading, **compress your entire project** into a [`.zip`](../faq/general-questions/wip-how-to-compress.md) file.
{% endstep %}

{% step %}
Uploading to the Dashboard.

{% stepper %}
{% step %}
Go to the **Discloud Dashboard**.
{% endstep %}

{% step %}
Click **"Upload"** and select your `.zip` file.
{% endstep %}

{% step %}
Wait for the upload to complete.
{% endstep %}
{% endstepper %}

{% hint style="danger" %}
During the upload, avoid refreshing the page to prevent any issues with your application. If this happens, you might need to remove the application and repeat the upload process.
{% endhint %}
{% endstep %}

{% step %}
Deployment Process.

* Once uploaded, Discloud will **automatically start your application**.
* If your project is correctly configured and doesn’t exceed the **RAM limit**, it should be online within seconds.
* You can check its status via the Dashboard.
{% endstep %}
{% endstepper %}

***

## **❓ Still need help?**

Check the [**FAQ Section**](broken-reference) or join our [**Discord Server**](https://discord.discloudbot.com/) for support.

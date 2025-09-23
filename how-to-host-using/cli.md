---
description: Learn how to host your applications quickly and easily using one of our CLIs.
icon: terminal
---

# CLI

The **Discloud CLI** allows you to **deploy and manage your applications** directly from the command line, providing a fast and efficient way to interact with your app.

***

## 🔑 **Windows Execution Policy (Only for Windows Users)**

### 🛠️ What is Execution Policy? <a href="#what-is-execution-policy" id="what-is-execution-policy"></a>

The Execution Policy protects your system by limiting the execution of unsigned scripts. The **RemoteSigned** mode allows local scripts to run without signatures but requires a signature for scripts downloaded from the internet.

### ❓ **How to Enable Script Execution**

{% stepper %}
{% step %}
Open PowerShell as Administrator.
{% endstep %}

{% step %}
Run the following command.

```powershell
Set-ExecutionPolicy RemoteSigned -Scope CurrentUser
```
{% endstep %}

{% step %}
Confirm the change by typing `Y` and pressing Enter.
{% endstep %}

{% step %}
Restart PowerShell and try running Discloud CLI commands again.
{% endstep %}
{% endstepper %}

***

## 🔧 Installing the Discloud CLI

{% tabs %}
{% tab title="📦 Node.js" %}
{% stepper %}
{% step %}
Prerequisite.

Ensure you have [NodeJS](../development-environment/local-environment/nodejs.md) installed on your system.
{% endstep %}

{% step %}
Install the CLI.

```bash
npm install -g discloud.app
```
{% endstep %}

{% step %}
**Reopen the terminal** to apply the changes.
{% endstep %}

{% step %}
Verify Installation.

After installation, run the following command to verify if the CLI was installed correctly:

```bash
discloud --version
```

{% hint style="success" %}
If the CLI version is displayed, the installation was successful.
{% endhint %}

{% hint style="info" %}
#### **CLI Update**

#### To update the CLI, run the following command:

```bash
npm update -g discloud-cli
```
{% endhint %}
{% endstep %}

{% step %}
Login.

To access CLI functionalities, you need to log in with your Discloud credentials. Run the following command and paste your [Discloud API Token](../api-and-integrations/api-overview/authentication.md):

```bash
discloud --login
```
{% endstep %}
{% endstepper %}

{% hint style="info" %}
#### **Official CLI Repository**

The NodeJS CLI is an open-source project. You can contribute, report bugs, and suggest improvements in the official repository.

{% embed url="https://github.com/discloud/cli" %}
{% endhint %}
{% endtab %}
{% endtabs %}

***

## 🚀 Deploying Your Application

Once installed and configured, you can **deploy your application** in just a few steps.

{% stepper %}
{% step %}
Preparing your project.

* Ensure your project contains all required files:
  * [**`discloud.config`**](../configurations/discloud.config/) (configuration file).
  * Necessary **dependencies** for your programming language (e.g., `package.json` for Node.js, `requirements.txt` for Python).
* **Check the** [**Languages Guide**](../development-environment/supported-languages/) to make sure your project is properly structured.
{% endstep %}

{% step %}
Uploading your application.

To deploy your project, navigate to your application folder and run:

```bash
discloud up
```

* The CLI will **automatically compress** your project and upload it.
* Once completed, your application will **start running** on Discloud.

{% hint style="info" %}
#### **To check your app status, use:**

```sh
discloud status
```
{% endhint %}
{% endstep %}
{% endstepper %}

***

## 📌 Tips & Tricks

### ✨ **Using `discloud init` to Auto-Generate Configuration**

Instead of manually creating the **`discloud.config`** file, you can generate it automatically using:

```sh
discloud init
```

* This command prompts you to enter **basic configuration details** (e.g., name, main file, RAM, etc).
* It then **generates the** [**`discloud.config`**](../configurations/discloud.config/) **file** for you, making deployment easier.

### 📂 **Using `.discloudignore` to Exclude Files**

If you want to **exclude certain files or directories** from being uploaded, you can create a [`.discloudignore`](../configurations/.discloudignore.md) file in the root of your project.

***

## **❓ Still need help?**

Check the [**FAQ Section**](broken-reference) or join our [**Discord Server**](https://discord.discloudbot.com/) for support.

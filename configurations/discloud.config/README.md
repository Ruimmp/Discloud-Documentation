---
description: >-
  Learn everything about the configuration file for hosting applications on
  Discloud.
icon: gear
---

# discloud.config

## 📄 What is `discloud.config` and what is it used for?

It is a configuration file that streamlines the process of deploying your applications to Discloud. With this file, you can easily configure the information for each application you upload to the hosting service.

***

## 📂 **Placement of the `discloud.config` File**

**✅ Correct Placement**

The `discloud.config` file <mark style="color:yellow;">**must be in the**</mark> [<mark style="color:yellow;">**root**</mark> <mark style="color:yellow;"></mark><mark style="color:yellow;">of your project</mark>](../../faq/general-questions/what-is-the-root-of-the-project.md).

```bash
your-project/           # ← ROOT DIRECTORY
├── discloud.config     # ✅ REQUIRED HERE
├── package.json        # Example root file
├── src/                # Source code folder
│   └── index.js        # Main application file
├── .gitignore          # Config files
└── README.md           # Documentation
```

**❌ Invalid Locations**

These placements will cause deployment failures:

```bash
your-project/
├── src/
│   └── discloud.config   # ❌ SUBFOLDER ERROR
├── config/
│   └── discloud.config   # ❌ SUBFOLDER ERROR
└── .github/
    └── discloud.config   # ❌ HIDDEN FOLDER ERROR
```

***

## 🛠️ Configuration options

See below all the configuration options for the `discloud.config` file. [Click here to check out some examples of different applications](./#examples-of-discloud.config-files).

{% tabs %}
{% tab title="📑 Information" %}
Define information for your application on the hosting platform, such as `NAME` and `AVATAR`. This allows you to easily identify your application on the dashboard or in the Visual Studio Code extension. See:

{% code title="discloud.config" %}
```properties
NAME=MyApp
AVATAR=https://i.imgur.com/bWhx7OT.png
# ...
```
{% endcode %}

* `NAME` - determines the name of your application on the hosting platform.
* `AVATAR` - uses the image URL as the avatar for your application on the hosting platform.
{% endtab %}

{% tab title="🖥️ Application" %}
For your application to start correctly on the hosting, you need to define its type using the `TYPE` option, set the entry point with the `MAIN` option, specify the maximum `RAM` it can use with the `RAM` option, and indicate the [language version](versions.md) with the `VERSION` option. See below:

{% code title="discloud.config" %}
```properties
# ...
TYPE=bot
MAIN=index.js
RAM=100
VERSION=latest
# ...
```
{% endcode %}

* `TYPE` - can have two values: **bot** or **site**.
* `MAIN` - should contain the path to the [main file](../../faq/general-questions/wip-what-is-the-main-file.md) of your application.
* `RAM` - determines the maximum amount of RAM available for the application.
* `VERSION` - specifies the [language version](versions.md) of your project.

{% hint style="info" %}
If the `TYPE` is set to **site**, you must also define the `ID` option with your subdomain. [See more here.](../../faq/general-questions/wip-how-to-create-a-subdomain.md)
{% endhint %}

<pre class="language-properties" data-title="discloud.config"><code class="lang-properties"><strong>TYPE=site
</strong><strong>ID=your-subdomain
</strong>MAIN=index.js
RAM=100
VERSION=latest
# ...
</code></pre>

{% hint style="warning" %}
To host a **website**, a minimum of **512MB of RAM** is required, along with a [**Platinum Plan**](https://discloud.com/plans).
{% endhint %}
{% endtab %}

{% tab title="🧩 Resources" %}
Depending on the programming language of your project, you can define which commands will be executed for the build process and the command to start the application using the `BUILD` and `START` properties.

To enable automatic restart in case of failures, set the `AUTORESTART` option to **true** (available only for [**Platinum Plan**](https://discloud.com/plans) or higher).

You can install [packages](apt.md) using the `APT` option.

{% code title="discloud.config" %}
```properties
# ...
BUILD=npm run build
START=npm run start
AUTORESTART=true
APT=tools
```
{% endcode %}

* `BUILD` - defines the command or script for compiling the project.
* `START` - defines the command or script for starting the project.
* `AUTORESTART` - ensures that the application restarts automatically in case of failure.
* `APT` - allows you to specify a list of [packages](../../api-and-integrations/api-overview/) to be installed.
{% endtab %}

{% tab title="🐋 Dockerfile" %}
If you are deploying a project with a [**Dockerfile**](dockerfile.md), you will have additional options available.

* Set a boolean value for the `VLAN` option to enable or disable networking between applications deployed with a **Dockerfile**.
* Customize the Docker network name of your application using the `HOSTNAME` option.

{% code title="discloud.config" %}
```properties
# ...
MAIN=Dockerfile
VLAN=true
HOSTNAME=expressapi
```
{% endcode %}

* Setting `MAIN` as your **Dockerfile** enables the use of the following options:
  * `VLAN` - Enables or disables the use of Docker networks.
  * `HOSTNAME` - Defines the name of the Docker network for your application.
{% endtab %}
{% endtabs %}

{% hint style="info" %}
## ⚠️ Mandatory options in your **`discloud.config`**

**Only one field is required**:

```ini
MAIN=index.js
```

**All other fields are optional** and will use smart defaults if omitted:

* `TYPE` defaults to `bot`
* `RAM` defaults to `100` (MB)
* `VERSION` defaults to `latest`
{% endhint %}

***

## 🪅 Examples of **`discloud.config`** files

> See below examples of **discloud.config** files for [🤖 Discord Bots](./#discord-bots), [🌐 Websites and APIs](./#websites-and-apis), and [🐋 Applications with Dockerfile](./#applications-with-dockerfile).

{% tabs %}
{% tab title="🤖 Discord bots" %}
{% tabs %}
{% tab title="🟨Simple JS Bot" %}
Discord bot made in JavaScript where the entry point is the **index.js** file in the root of the project.

{% code title="discloud.config" %}
```properties
NAME=Lorito
TYPE=bot
MAIN=index.js
RAM=100
VERSION=latest
```
{% endcode %}
{% endtab %}

{% tab title="🟦 Bot with TS" %}
Bot made in TypeScript where the entry point is the **index** file inside the **build** folder. The application will start by executing the **start** script from the **package.json** file.

{% code title="discloud.config" %}
```properties
NAME=Mee8
TYPE=bot
MAIN=build/index.js
START=npm run start
RAM=200
VERSION=latest
```
{% endcode %}
{% endtab %}

{% tab title="🐍 Bot with PY" %}
Discord bot made in Python where the entry point is the **main.py** file in the root of the project.

{% code title="discloud.config" %}
```properties
NAME=Dyna
TYPE=bot
MAIN=main.py
RAM=300
VERSION=latest
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="🌐 Websites and APIs" %}
{% tabs %}
{% tab title="📄 Simple HTML website" %}
Simple website with plain HTML, using the **"friendbook"** subdomain from the user's account.

{% code title="discloud.config" %}
```properties
NAME=Friendbook
TYPE=site
MAIN=index.html
RAM=512
VERSION=latest
ID=friendbook
```
{% endcode %}
{% endtab %}

{% tab title="🟢 Web API with Express" %}
Web API built with **Express.js**, where the entry file is **index.js** inside the **server** folder. The application will start by executing the **start** script from the **package.json** file.

{% code title="discloud.config" %}
```properties
NAME=Crud cinema
TYPE=site
MAIN=server/index.js
START=npm run start
RAM=512
VERSION=latest
ID=moviemark
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="🐋 Applications with Dockerfile" %}
{% tabs %}
{% tab title="🍃 MongoDB Server" %}
MongoDB database server that will be consumed by another application, where the Docker network name will be **mongoserver**.

{% code title="discloud.config" %}
```properties
NAME=MongoDB Server
TYPE=bot
MAIN=Dockerfile
RAM=512
VERSION=latest
VLAN=true
HOSTNAME=mongoserver
```
{% endcode %}
{% endtab %}

{% tab title="🤖 Discord Bot" %}
Discord bot made in **TypeScript** with **Mongoose**, which will be built and started in the **Dockerfile** and will be able to access other Docker networks of the user.

{% code title="discloud.config" %}
```properties
NAME=Ticket Bot mongoose
TYPE=bot
MAIN=Dockerfile
RAM=512
VERSION=latest
VLAN=true
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}
{% endtabs %}

***

## ⚙️ **Configuration options**

The `discloud.config` file contains essential settings for your Discloud application. Below are the **available configuration options** along with their respective limits and descriptions.

<table><thead><tr><th width="147" align="center">Option</th><th width="258" align="center">Limit / Values</th><th align="center">Description</th></tr></thead><tbody><tr><td align="center"><strong>NAME</strong></td><td align="center"><code>1 - 30 characters</code></td><td align="center">The name of your application (used for display purposes).</td></tr><tr><td align="center"><strong>AVATAR</strong></td><td align="center"><code>Image URL (.gif, .jpeg, .jpg, .png)</code></td><td align="center">A URL to the application's avatar. Supported formats: <strong>GIF, JPEG, JPG, PNG</strong>.</td></tr><tr><td align="center"><strong>TYPE</strong></td><td align="center"><code>bot / site</code></td><td align="center">Defines whether the application is a <strong>bot</strong> or a <strong>website</strong>.</td></tr><tr><td align="center"><strong>MAIN</strong></td><td align="center"><code>Relative file path</code></td><td align="center">Specifies the <strong>main file</strong> that should be executed in the project folder.</td></tr><tr><td align="center"><strong>RAM</strong></td><td align="center"><code>100 - 32000 MB</code></td><td align="center">The <strong>amount of RAM</strong> allocated to the application (<strong>varies by</strong> <a href="https://discloud.com/plans"><strong>plan</strong></a>).</td></tr><tr><td align="center"><strong>VERSION</strong></td><td align="center"><code>latest / current / suja / specific</code></td><td align="center">Defines the <a href="versions.md"><strong>versioning</strong></a> options for the environment and dependencies.</td></tr><tr><td align="center"><strong>ID</strong></td><td align="center"><code>User-defined subdomains</code></td><td align="center">Custom subdomain for your application (<a href="../../how-to-host/websites-and-apis.md">for websites only</a>).</td></tr><tr><td align="center"><strong>BUILD</strong></td><td align="center"><em>(Custom build commands)</em></td><td align="center">If specified, defines <strong>commands to run before the application starts</strong> (e.g., installing dependencies).</td></tr><tr><td align="center"><strong>START</strong></td><td align="center"><em>(Custom start command)</em></td><td align="center">Overrides the default start command to launch the application.</td></tr><tr><td align="center"><strong>AUTORESTART</strong></td><td align="center"><code>true / false</code></td><td align="center">Determines whether the app should <strong>automatically restart</strong> if it crashes.</td></tr><tr><td align="center"><strong>VLAN</strong></td><td align="center"><code>true / false</code></td><td align="center">Enables <strong>Virtual LAN (VLAN)</strong> for internal networking between applications.</td></tr><tr><td align="center"><strong>HOSTNAME</strong></td><td align="center"><em>(Custom hostname)</em></td><td align="center">Specifies a custom hostname for the application.</td></tr><tr><td align="center"><strong>APT</strong></td><td align="center"><em>(List of packages)</em></td><td align="center">Installs additional <strong>Linux dependencies</strong> required by your app. <a href="apt.md"><strong>View available packages</strong></a>.</td></tr></tbody></table>

***

---
description: Practical guide to host NestJS applications on Discloud.
icon: feather
---

# NestJS

## 🧭 Introduction

This step-by-step guide shows how to prepare, configure, and deploy a **NestJS** application on Discloud.

The process involves building your TypeScript code into the `dist` folder and running the compiled JavaScript on port `8080`. NestJS apps are straightforward to deploy because the framework handles routing, dependency injection, and module organization automatically.

---

## 📋 Requirements

{% hint style="success" %}
A [Platinum plan or higher](https://discloud.com/plans) is required to host websites or APIs.
{% endhint %}

{% hint style="success" %}
[A subdomain must be created](../../faq/general-questions/how-to-create-a-subdomain.md) before deployment.
{% endhint %}

{% hint style="danger" %}
Port `8080` is mandatory – applications must listen on this port.
{% endhint %}

---

## 🧱 Local prerequisites

Before continuing, you will need:

- **Node.js** installed on your machine.
- A **NestJS project** created (e.g. `nest new my-app`).
- A **Discloud account** with a **configured subdomain**.
- Optionally: **Git**, **VSCode**, and/or the **Discloud CLI** to make the workflow easier.

If you are not yet familiar with the local environment, check:

{% content-ref url="../../development-environment/local-environment/nodejs.md" %}
[nodejs.md](../../development-environment/local-environment/nodejs.md)
{% endcontent-ref %}

---

## 🧹 Preparing project files

Before compressing your project into a `.zip`, create a [**`.discloudignore`**](../../configurations/.discloudignore.md) file in the project root to exclude unnecessary files and folders from the upload:

```
node_modules/
dist/
.env
.env.local
.git
.vscode/
package-lock.json
```

{% hint style="info" %}
The `.discloudignore` file works similarly to `.gitignore`, but it is used by Discloud to ignore files at upload time.
{% endhint %}

---

## 🔧 TypeScript Configuration – `tsconfig.build.json`

Ensure your `tsconfig.build.json` (or `tsconfig.json`) is set to output to the `dist` folder. Here's a typical configuration:

```json
{
  "extends": "./tsconfig.json",
  "compilerOptions": {
    "outDir": "./dist",
    "rootDir": "./src",
    "composite": false,
    "incremental": false
  },
  "exclude": ["node_modules", "dist"]
}
```

{% hint style="danger" %}
It is important that **`compilerOptions.outDir`** is set to `"dist"`, as Discloud will look for your compiled app there.
{% endhint %}

---

## 🚀 Main entry point – `src/main.ts`

Ensure your `src/main.ts` listens on **port 8080** and accepts the port from environment variables. Here's a typical setup:

```ts
import { NestFactory } from "@nestjs/core";
import { AppModule } from "./app.module";

async function bootstrap() {
  const app = await NestFactory.create(AppModule);
  const port = process.env.PORT ? Number(process.env.PORT) : 8080;

  await app.listen(port, "0.0.0.0");
  console.log(`Server is running on http://0.0.0.0:${port}`);
}

bootstrap();
```

{% hint style="danger" %}
**Important:**

- **Port 8080 is mandatory.** Even if you set `PORT` in your `.env` file, it must be `8080`.
- Bind to `0.0.0.0` (not `localhost`) so external traffic can reach your app.
  {% endhint %}

---

## 📦 `package.json` – recommended scripts

Inside your [`package.json`](../../development-environment/supported-languages/javascript/package.json.md), ensure the build and start scripts are correctly defined:

```json
{
  "scripts": {
    "start": "node dist/main",
    "start:dev": "nest start --watch",
    "build": "nest build"
  }
}
```

{% hint style="info" %}

- `build` – compiles TypeScript to `dist` via the Nest CLI.
- `start` – runs the compiled app from the `dist` folder.
- `start:dev` – runs in watch mode locally (not needed for Discloud).
  {% endhint %}

---

## ⚙️ `discloud.config` – example

Here's a typical configuration for a NestJS app:

```
TYPE=site
BUILD=npm run build
START=npm run start
RAM=512
VERSION=latest
ID=my-nestjs-app
```

For detailed information about each configuration parameter and all available options, refer to the complete guide:

{% content-ref url="../../configurations/discloud.config/" %}
[discloud.config](../../configurations/discloud.config/)
{% endcontent-ref %}

{% hint style="warning" %}
Make sure to adjust the `ID` field to match your registered subdomain from the Discloud dashboard.
{% endhint %}

---

## 🧪 Testing locally (production build)

Before uploading to Discloud, verify your app builds and runs correctly:

{% stepper %}
{% step %}
Build the project locally:

```bash
npm run build
```

This generates the `dist` folder with compiled JavaScript.
{% endstep %}

{% step %}
Test the production build:

```bash
npm run start
```

Check that the server starts and responds to requests (e.g., via `curl http://localhost:8080`).
{% endstep %}

{% step %}
Stop the server and proceed to deployment.
{% endstep %}
{% endstepper %}

---

## 🔐 Environment variables

In NestJS, environment variables are typically accessed via `process.env`:

- Define variables via the **Discloud Dashboard**, **CLI**, or **API**.
- Common patterns include `DATABASE_URL`, `API_KEY`, `REDIS_URL`, etc.

Example in a service:

```ts
import { Injectable } from "@nestjs/common";

@Injectable()
export class ConfigService {
  getDatabaseUrl() {
    return process.env.DATABASE_URL || "sqlite:memory";
  }
}
```

{% hint style="info" %}
For better type safety and validation, consider using the `@nestjs/config` package to manage environment variables.
{% endhint %}

---

## 🗂️ Recommended final project structure

A typical NestJS project structure for Discloud might look like:

```
my-nest-app/
├─ discloud.config
├─ .discloudignore
├─ package.json
├─ tsconfig.json
├─ tsconfig.build.json
├─ src/
│  ├─ main.ts
│  ├─ app.module.ts
│  ├─ app.controller.ts
│  └─ app.service.ts
└─ dist/  (generated after build)
```

---

## 🚀 Deploying to Discloud

You can deploy your NestJS app using any of the supported methods.

{% content-ref url="../../how-to-host-using/dashboard.md" %}
[dashboard.md](../../how-to-host-using/dashboard.md)
{% endcontent-ref %}

{% content-ref url="../../how-to-host-using/discord-bot.md" %}
[discord-bot.md](../../how-to-host-using/discord-bot.md)
{% endcontent-ref %}

{% content-ref url="../../how-to-host-using/visual-studio-code.md" %}
[visual-studio-code.md](../../how-to-host-using/visual-studio-code.md)
{% endcontent-ref %}

{% content-ref url="../../how-to-host-using/cli.md" %}
[cli.md](../../how-to-host-using/cli.md)
{% endcontent-ref %}

---

## 🛠️ Troubleshooting (common errors)

|                                    |                                                                                                                                                           |
| ---------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **App does not open / wrong port** | Check if NestJS is listening on port `8080` (`process.env.PORT \|\| 8080` in `main.ts`).                                                                  |
| **`dist` folder not found**        | Verify `tsconfig.build.json` has `"outDir": "./dist"` and run `npm run build` locally to confirm.                                                         |
| **Plan / permission error**        | Confirm that your account has the **correct plan** for websites/APIs.                                                                                     |
| **Subdomain not configured**       | Make sure you followed the **subdomain guide** before deploying.                                                                                          |
| **Build errors**                   | <ul><li>Run locally: `npm run build` and fix any errors before uploading.</li><li>Check that all **dependencies** are listed in `package.json`.</li></ul> |
| **Errors when starting (`START`)** | <ul><li>Verify that the `start` script is correct.</li><li>Follow the **Discloud logs** to see the exact error message.</li></ul>                         |

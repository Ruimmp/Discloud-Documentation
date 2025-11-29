---
description: >-
  Saiba como configurar o Puppeteer na Discloud, incluindo dependências e
  ajustes de RAM, para garantir o funcionamento correto em ambientes de
  containers.
icon: toolbox
---

# Puppeteer

## 📌 **Requisitos**

Para usar **Puppeteer** na Discloud, é recomendado um mínimo de **512 MB de RAM** para tarefas básicas. No entanto, dependendo da complexidade da sua aplicação, **mais RAM** pode ser necessária.

{% hint style="warning" %}
**Se o Puppeteer não funcionar corretamente (ex.: nenhum código QR nos logs, travamentos), aumente a RAM alocada!**
{% endhint %}

***

## 📦 **Adicionando Puppeteer**

O Puppeteer requer dependências adicionais do sistema. Você deve adicionar **`puppeteer`** ao campo [`APT`](discloud.config/apt.md) no seu arquivo [**`discloud.config`**](discloud.config/).

<pre class="language-ini" data-title="discloud.config"><code class="lang-ini"><a data-footnote-ref href="#user-content-fn-1"># ...</a>
APT=tools, puppeteer
# ...
</code></pre>

***

## ⚙️ **Configurando Puppeteer**

Como **Puppeteer é executado em um ambiente containerizado**, você deve adicionar o argumento `--no-sandbox` para garantir que funcione corretamente.

```javascript
const puppeteer = require("puppeteer");

(async () => {
  const browser = await puppeteer.launch({
    args: ["--no-sandbox"],
  });

  const page = await browser.newPage();
  await page.goto("https://example.com");

  console.log(await page.title());
  await browser.close();
})();
```

{% hint style="info" %}
#### **Por que `--no-sandbox`?**

Executar Puppeteer dentro de um container **requer desabilitar o sandbox** para impedir que restrições de segurança bloqueiem a execução.
{% endhint %}

***

## ⚙️ **Usando Puppeteer com `whatsapp-web.js`**

Como [**`whatsapp-web.js`**](https://wwebjs.dev/) também usa **Puppeteer** para geração de código QR e interações em segundo plano, você deve **incluir `--no-sandbox`** na sua configuração.

```javascript
const { Client } = require("whatsapp-web.js");

const client = new Client({
  puppeteer: {
    args: ["--no-sandbox"],
  },
});

client.initialize();
```

{% hint style="info" %}
#### **Solução de Problemas com Código QR:**

* Se o **código QR não aparecer** nos logs da Discloud, **aumente a RAM alocada**.
* Quanto mais complexas suas interações com o WhatsApp, **mais RAM o Puppeteer precisará** para funcionar adequadamente.
{% endhint %}

[^1]: **Note:** The **`...`** only indicate the continuation of other previous or subsequent options that are not relevant to mention on this page.

---
description: >-
  Saiba como configurar o Puppeteer na Discloud, incluindo dependências e
  ajustes de RAM, para garantir o funcionamento correto em ambientes de
  containers.
---

# 🧰 Puppeteer

## 📝 Requisitos

Para o uso do Puppeteer na Discloud, recomenda-se pelo menos **512 MB de RAM** para tarefas básicas. Dependendo da complexidade da aplicação, mais RAM pode ser necessária.

***

## 📦 Adicionar o Puppeteer no APT

Para instalar o Puppeteer via [APT](pacotes-apt.md), edite o arquivo [`discloud.config`](discloud-config.md) e adicione `puppeteer` na linha `APT`. Veja o exemplo:

```ini
...
APT=tools, puppeteer
...
```

***

## ⚙️ Configurando o Puppeteer

Para garantir o funcionamento correto do **Puppeteer** em um container, é necessário adicionar o argumento `--no-sandbox` na instrução `puppeteer.launch();`, como demonstrado no exemplo a seguir:

```js
const browser = await puppeteer.launch({
  args: ['--no-sandbox']
});
```

***

## ⚙️ Configuração com WhatsApp-web.js

Como o **whatsapp-web.js** utiliza o **Puppetter** (para geração do QR code, e interações em segundo plano), é necessário adicionar o argumento `--no-sandbox` às opções do `puppetter`, como no exemplo a seguir:

```js
const client = new Client({
	puppeteer: {
		args: ['--no-sandbox'],
	}
});
```

{% hint style="info" %}
Em caso de memória RAM insuficiente, o **QR code poderá não aparecer nas logs da Discloud**, para resolver isto aumente a memória do seu app como mencionado nos requisitos acima, para que o Puppeteer funcione como esperado.
{% endhint %}

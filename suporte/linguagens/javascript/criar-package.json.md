---
description: Aprenda a hospedar seu bot em JavaScript na DisCloud
---

# 📄 Criar o package.json

O arquivo `package.json` é uma espécie de manifesto para seu projeto. Ele pode fazer um monte de coisas, é também onde o **npm** armazena os **nomes** e **versões** de todos os **pacotes instalados** que o seu projeto depende.

### Como criar o arquivo `package.json`?

Abra o Terminal no diretório do seu projeto (Windows use: **Shift+Botão Direito** e clique em **Open PowerShell**) e digite:

```
npm init -y
```

{% hint style="info" %}
Você precisa do **NodeJS e npm** instalado no seu computador, caso não esteja instalado siga as instruções abaixo.
{% endhint %}

{% content-ref url="../../../ambiente-local/instalar/nodejs.md" %}
[nodejs.md](../../../ambiente-local/instalar/nodejs.md)
{% endcontent-ref %}

### Colocando dependências no seu `package.json`

#### Instalando o [discord.js](https://www.npmjs.com/package/discord.js?source=post\_page-----7b5fe27cb6fa----------------------)

Para instalar digite

```
npm install discord.js
```

O seu `package.json` deve estar com a seguinte aparência.

{% code title="package.json" %}
```json
{
  "name": "discloudbot",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {
    "discord.js": "^14.0.3"
  }
}
```
{% endcode %}

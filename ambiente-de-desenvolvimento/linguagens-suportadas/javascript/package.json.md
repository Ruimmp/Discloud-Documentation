---
description: >-
  Aprenda como gerar e configurar o arquivo 'package.json', definindo as
  dependências essenciais para hospedar seu projeto JavaScript no Discloud.
---

# package.json

## 🗂️ O que é `package.json`?

O arquivo `package.json` é essencial para gerenciar metadados e dependências de projetos Node.js. Ele garante que as bibliotecas necessárias sejam instaladas automaticamente ao hospedar sua aplicação no Discloud.

---

## 🛠️ Como Criar `package.json`

Para gerar o arquivo `package.json` para seu projeto, siga os passos abaixo:

{% stepper %}
{% step %}
**Abra o terminal no diretório do seu projeto**

No Windows, use **Shift + Clique Direito** e selecione "Abrir PowerShell".
{% endstep %}

{% step %}
**Execute o seguinte comando para criar o `package.json` automaticamente:**

```bash
npm init -y
```

Este comando criará um arquivo `package.json` no diretório do seu projeto.
{% endstep %}
{% endstepper %}

---

## 📝 Estrutura do `package.json`

Após a criação, o arquivo `package.json` deve se parecer com isso:

{% code title="package.json" %}

```json
{
  "name": "discloud",
  "version": "1.0.0",
  "description": "",
  "main": "index.js",
  "scripts": {
    "test": "echo \"Error: no test specified\" && exit 1"
  },
  "keywords": [],
  "author": "",
  "license": "ISC",
  "dependencies": {}
}
```

{% endcode %}

{% hint style="info" %}
Se você quiser hospedar um bot **Discord.js** ou qualquer outro framework, você precisará adicionar dependências ao `package.json`. Verifique a próxima seção para aprender como fazer isso.
{% endhint %}

---

## 📦 Adicionando Dependências

Para adicionar dependências, use o comando `npm install`, que adicionará automaticamente as bibliotecas necessárias ao `package.json`.

**Exemplo: Instalar `discord.js`**

```bash
npm install discord.js
```

Após instalar, seu `package.json` será automaticamente atualizado para incluir `discord.js` nas dependências:

{% code title="package.json" %}

```json
{
  "name": "discloud",
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

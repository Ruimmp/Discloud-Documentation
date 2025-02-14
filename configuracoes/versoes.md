---
description: >-
  Saiba como configurar e alterar as versões de linguagens como Node.js, Python,
  Java e outras em suas aplicações hospedadas na Discloud.
---

# 📊 Versões

## 🏗️ Configuração de Versão da Linguagem

Na **Discloud**, é possível configurar a versão da linguagem que sua aplicação utilizará, conforme necessário, seja para aproveitar novos recursos ou manter compatibilidade com versões mais antigas.

***

## ⚙️ Como Utilizar

Para definir a versão de uma linguagem, inclua a seguinte linha no arquivo `discloud.config`:

{% code title="discloud.config" %}
```ini
...
VERSION=current
...
```
{% endcode %}

{% hint style="info" %}
**Observação**\
\
Os três pontos (`...`) indicam continuidade de outras configurações no `discloud.config`. A linha `VERSION` deve ser ajustada conforme as opções abaixo para a linguagem desejada.
{% endhint %}

***

## 📋 Versões Disponíveis

{% tabs %}
{% tab title="Node.js" %}
| latest  |
| ------- |
| current |
| 18.x.x  |
| 16.13.2 |
| 14.18.3 |
| suja    |
{% endtab %}

{% tab title="Python" %}
| latest |
| ------ |
| 3.11   |
| 3.10   |
| 3.9.10 |
| 3.9    |
| 2.7    |
| suja   |
{% endtab %}

{% tab title="Java" %}
| latest |
| ------ |
| 18.x.x |
| 17.x.x |
| 16.x.x |
{% endtab %}

{% tab title="Ruby" %}
| latest |
| ------ |
| 3.1.0  |
| 2.7.5  |
{% endtab %}

{% tab title="Go" %}
| latest  |
| ------- |
| 1.16.13 |
| 1.7.6   |
{% endtab %}

{% tab title="PHP" %}
| latest |
| ------ |
{% endtab %}

{% tab title="Rust" %}
| latest |
| ------ |
| suja   |
{% endtab %}
{% endtabs %}

{% hint style="info" %}
**Informações Gerais sobre as Versões**\


Para cada linguagem suportada, a opção `latest` define a versão estável mais recente (recomendada). Para linguagens específicas, há as seguintes opções adicionais:

* **Node.js**: `current` para a versão mais recente, e `suja` para uma versão com muitos pacotes pré-instalados (use como último recurso).
* **Python, Java, Ruby, Go, PHP, Rust**: `latest` sempre define a versão mais recente disponível para cada uma dessas linguagens.
{% endhint %}

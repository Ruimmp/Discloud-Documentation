# ⚙ Configurar

O `discloud.config` é um arquivo de configurações, que agiliza o processo de upload de suas aplicações para a DisCloud.

## :gear: Como Utilizar

Detalhes para cada opção

![](../../.gitbook/assets/discloud-config-pt.png)

> Consulte a lista de opções para: [VERSION](version.md), [APT](apt.md)

> Se estiver fazendo um `bot` ou um `site` pode se basear nos exemplos abaixo:

{% tabs %}
{% tab title="🤖 Exemplo para Bot" %}
{% hint style="info" %}
Para hospedar um bot precisa de `100MB` de ram no mínimo
{% endhint %}

{% code title="discloud.config" %}
```tsconfig
NAME=Meubot
AVATAR=https://...
TYPE=bot
MAIN=index.js
RAM=100
AUTORESTART=false
VERSION=latest
APT=tools
```
{% endcode %}
{% endtab %}

{% tab title="🌎 Exemplo para Site" %}
{% hint style="info" %}
Para hospedar um site precisa de `512MB` de ram no mínimo
{% endhint %}

{% code title="discloud.config" %}
```tsconfig
NAME=MeuSite
AVATAR=https://...
ID=subdomain
TYPE=site
MAIN=index.js
RAM=512
AUTORESTART=false
VERSION=latest
APT=tools
```
{% endcode %}
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Coloque o `discloud.config` na raiz do seu projeto e não se esqueça de incluir no seu [.zip](../../suporte/faq/zip.md)
{% endhint %}

![](../../.gitbook/assets/vscode-discloud.config.png)

## :cloud: Fazendo o Upload

Com o seu [.zip ](../../suporte/faq/zip.md)criado com o `discloud.config` chegou a hora do Upload, para utilizar é muito simples!

> * No canal de comandos digite `.upconfig` (ou abreviação `.upc`)
> * Entre no canal que o bot acabou de criar e coloque o seu .zip

![](../../.gitbook/assets/pr-upc.gif)

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
Para hospedar um bot precisa de **100MB** de RAM no mínimo
{% endhint %}

{% code title="discloud.config" %}
```tsconfig
NAME=Meubot
AVATAR=https://i.imgur.com/bWhx7OT.png
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
Para hospedar um site precisa de **512MB** de RAM no mínimo, e um [Plano Platina](https://discloudbot.com/plans)
{% endhint %}

{% code title="discloud.config" %}
```tsconfig
NAME=MeuSite
AVATAR=https://i.imgur.com/bWhx7OT.png
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

## :cloud: Fazendo o upload pelo site

Com o seu [.zip ](../../suporte/faq/zip.md)criado com o `discloud.config` chegou a hora do Upload, para utilizar é muito simples!

<figure><img src="../../.gitbook/assets/g.gif" alt=""><figcaption><p>upload pelo site</p></figcaption></figure>

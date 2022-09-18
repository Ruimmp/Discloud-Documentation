# Como utilizar o arquivo discloud.config?

#### O `discloud.config` é um arquivo de configurações predefinidas, para que você possa enviar as suas aplicações mais rapidamente, sem ter que digitar manualmente estas informações sempre que desejar fazer upload.

## :gear: Como Utilizar

![](../../.gitbook/assets/discloud-config-pt.png)

> Consulte a lista de opções para: [VERSION](discloud.config.md#versoes-disponiveis-no-version), [APT](discloud.config.md#pacotes-disponiveis-no-apt)

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
Coloque o `discloud.config` na raiz do seu projeto e não se esqueça de incluir no seu [.zip](zip.md)
{% endhint %}

![](../../.gitbook/assets/vscode-discloud.config.png)

## :cloud: Fazendo o Upload

Com o seu [.zip ](zip.md)criado com o `discloud.config` chegou a hora do Upload, para utilizar é muito simples!

> * No canal de comandos digite `.upconfig` (ou abreviação `.upc`)
> * Entre no canal que o bot acabou de criar e coloque o seu .zip

![](../../.gitbook/assets/pr-upc.gif)

### Pacotes disponíveis no `APT`

<table><thead><tr><th>Nome Do Pacote</th><th data-type="select" data-multiple>Dependências</th></tr></thead><tbody><tr><td>canvas</td><td></td></tr><tr><td>puppeteer</td><td></td></tr><tr><td>java</td><td></td></tr><tr><td>ffmpeg</td><td></td></tr><tr><td>libgl</td><td></td></tr><tr><td>tools</td><td></td></tr><tr><td>openssl</td><td></td></tr></tbody></table>

### Versões disponíveis no `VERSION`

> Selecione uma Linguagem para consultar

{% tabs %}
{% tab title="📦 JavaScript" %}
| Versões Disponíveis |   |
| ------------------- | - |
| latest              |   |
| current             |   |
| 16.13.2             |   |
| 14.18.3             |   |
| suja                |   |
{% endtab %}

{% tab title="🐍 Python" %}
| Versões Disponíveis |
| ------------------- |
| latest              |
| 3.9.10              |
| 2.7.18              |
| suja                |
{% endtab %}

{% tab title="☕ Java" %}
| Versões Disponíveis |
| ------------------- |
| latest              |
| 18.x.x              |
| 17.x.x              |
| 16.x.x              |
{% endtab %}

{% tab title="💎 Ruby" %}
| Versões Disponíveis |
| ------------------- |
| latest              |
| 3.1.0               |
| 2.7.5               |
{% endtab %}

{% tab title="🐿️ Go" %}
| Versões Disponíveis |
| ------------------- |
| latest              |
| 1.17.6              |
| 1.16.13             |
{% endtab %}

{% tab title="🐘 Php" %}
| Versões Disponíveis |
| ------------------- |
| latest              |
{% endtab %}

{% tab title="🦀 Rust" %}
| Versões Disponíveis |
| ------------------- |
| latest              |
| suja                |
{% endtab %}
{% endtabs %}

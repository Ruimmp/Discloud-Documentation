# ⚙ discloud.config

O `discloud.config` é um arquivo de configurações, que agiliza o processo de upload de suas aplicações para a DisCloud.\
Com este ficheiro você pode configurar facilmente cada app que enviar para DisCloud.

## :gear: Como Utilizar

> Se estiver fazendo um `bot` ou um `site` pode se basear nos exemplos abaixo:

{% tabs %}
{% tab title="🤖 Exemplo para Bot" %}
{% hint style="info" %}
Para hospedar um bot precisa de **100MB** de RAM no mínimo
{% endhint %}

> Clique nas opções para obter mais informações

<pre class="language-tsconfig" data-title="discloud.config"><code class="lang-tsconfig"><a data-footnote-ref href="#user-content-fn-1">NAME=Meubot</a>
<a data-footnote-ref href="#user-content-fn-2">AVATAR=https://i.imgur.com/bWhx7OT.png</a>
<a data-footnote-ref href="#user-content-fn-3">TYPE=bot</a>
<strong><a data-footnote-ref href="#user-content-fn-4">MAIN=index.js</a>
</strong><a data-footnote-ref href="#user-content-fn-5">RAM=100</a>
<a data-footnote-ref href="#user-content-fn-6">AUTORESTART=false</a>
<a data-footnote-ref href="#user-content-fn-7">VERSION=latest</a>
<a data-footnote-ref href="#user-content-fn-8">APT=</a>tools
</code></pre>

> Observação: As opções de <mark style="color:green;">`NOME`</mark> e <mark style="color:green;">`AVATAR`</mark> são para personalizar o nome e a imagem do seu app. Elas serão exibidas na dashboard, ou no Discord através de comandos do nosso bot (por exemplo: `.app`, `.status`).

<figure><img src="../../.gitbook/assets/dash-name-avatar-discloud-config.png" alt=""><figcaption><p>Exemplo na dashboard</p></figcaption></figure>
{% endtab %}

{% tab title="🌎 Exemplo para Site" %}
{% hint style="info" %}
Para hospedar um site precisa de **512MB** de RAM no mínimo, e um [Plano Platina](https://discloudbot.com/plans)
{% endhint %}

> Clique nas opções para obter mais informações

<pre class="language-tsconfig" data-title="discloud.config"><code class="lang-tsconfig"><a data-footnote-ref href="#user-content-fn-9">NAME=MeuSite</a>
<a data-footnote-ref href="#user-content-fn-10">AVATAR=https://i.imgur.com/bWhx7OT.png</a>
<strong><a data-footnote-ref href="#user-content-fn-11">ID=subdomain</a>
</strong><a data-footnote-ref href="#user-content-fn-12">TYPE=site</a>
<strong><a data-footnote-ref href="#user-content-fn-13">MAIN=index.js</a>
</strong><a data-footnote-ref href="#user-content-fn-14">RAM=512</a>
<a data-footnote-ref href="#user-content-fn-15">AUTORESTART=false</a>
<a data-footnote-ref href="#user-content-fn-16">VERSION=latest</a>
<a data-footnote-ref href="#user-content-fn-17">APT=</a>tools
</code></pre>
{% endtab %}
{% endtabs %}

{% hint style="info" %}
Coloque o `discloud.config` na raiz do seu projeto e não se esqueça de incluir no seu [.zip](../../suporte/faq/zip.md)
{% endhint %}

![](../../.gitbook/assets/vscode-discloud.config.png)

## :cloud: Fazendo o upload pelo site

Com o seu [.zip ](../../suporte/faq/zip.md)criado com o `discloud.config` chegou a hora do Upload, para utilizar é muito simples!

<figure><img src="../../.gitbook/assets/g.gif" alt=""><figcaption><p>upload pelo site</p></figcaption></figure>

[^1]: Nome da sua aplicação. <mark style="color:green;">(optional)</mark>

[^2]: URL com uma imagem para a sua aplicação (deve terminal em `.png` ou `.jpg`). <mark style="color:green;">(opcional)</mark>

[^3]: Tipo de aplicação `bot` ou `site`

[^4]: Nome ou caminho para o arquivo principal. Ex: `index.js` ou `src/index.js` <mark style="color:red;">(obrigatório mudar)</mark>

[^5]: Quantidade de memoria **RAM** em `MB`

[^6]: Reinício automático em caso de falhas na sua aplicação coloque `true` para ativar. Apenas [Plano Platina](https://discloudbot.com/plans) ou superior. <mark style="color:green;">(optional)</mark>

[^7]: Mude a [versão](version.md#versoes-disponiveis) utilizada na imagem do container da sua app.

[^8]: Instale pacotes [apt](apt.md#pacotes-disponiveis) no container da sua aplicação.

[^9]: Nome da sua aplicação <mark style="color:green;">(optional)</mark>

[^10]: URL com uma imagem para a sua aplicação (deve terminal em `.png` ou `.jpg`) <mark style="color:green;">(opcional)</mark>

[^11]: Subdomínio que será usado por sua aplicação, não se esqueça de [registrá-lo](../../suporte/hospedar/sites/) antes. <mark style="color:red;">(obrigatório mudar)</mark>

[^12]: Tipo de aplicação `bot` ou `site`

[^13]: Nome ou caminho para o arquivo principal. Ex: `index.js` ou `src/index.js` <mark style="color:red;">(obrigatório mudar)</mark>

[^14]: Quantidade de memoria **RAM** em `MB`.

[^15]: Reinício automático em caso de falhas na sua aplicação coloque `true` para ativar. Apenas [Plano Platina](https://discloudbot.com/plans) ou superior. <mark style="color:green;">(optional)</mark>

[^16]: Mude a [versão](version.md#versoes-disponiveis) utilizada na imagem do container da sua app.

[^17]: Instale pacotes [apt](apt.md#pacotes-disponiveis) no container da sua aplicação.

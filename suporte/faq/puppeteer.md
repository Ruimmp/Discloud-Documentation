# Configurar o Puppeteer

## :pencil:Requisitos

* **RAM**: 512 MB (recomendado para tarefas básicas)
  * A quantidade ideal de **RAM** pode variar consoante as especificidades de cada caso.

## :package:Adicione o Puppetter no [APT](../../discloud.config/configurar/apt.md) do [discloud.config](broken-reference)

Na linha **APT**, adicione o pacote `puppeteer` separado por vírgula e espaço após os pacotes já existentes, como no exemplo abaixo.

<pre class="language-typescript" data-title="discloud.config"><code class="lang-typescript">...
<strong>APT=tools, puppeteer
</strong>...
</code></pre>

## :gear:Configure o Puppeteer

Para garantir o funcionamento correto do **Puppeteer** em um container, é necessário adicionar o argumento `--no-sandbox` na instrução `puppeteer.launch();`, como demonstrado no exemplo a seguir:

<pre class="language-javascript"><code class="lang-javascript">const browser = await puppeteer.launch({
<strong>  args: ['--no-sandbox']
</strong>});
</code></pre>

## :gear:Configuração de dependências que utilizam o Puppeteer&#x20;

### <img src="https://wwebjs.dev/logo.png" alt="" data-size="line"> Configure o [whatsapp-web.js](https://wwebjs.dev/guide/#installation-on-no-gui-systems)

Como o **whatsapp-web.js** utiliza o **Puppetter** (para geração do QR code, e interações em segundo plano), é necessário adicionar o argumento `--no-sandbox` às opções do `puppetter`, como no exemplo a seguir:

<pre class="language-javascript"><code class="lang-javascript">const client = new Client({
	puppeteer: {
<strong>		args: ['--no-sandbox'],
</strong>	}
});
</code></pre>

{% hint style="info" %}
Em caso de memória RAM insuficiente, o **QR code poderá não aparecer nas logs da Discloud**, para resolver isto aumente a memória do seu app como mencionado nos requisitos acima, para que o Puppeteer funcione como esperado.
{% endhint %}

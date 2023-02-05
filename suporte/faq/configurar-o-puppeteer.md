# Configurar o Puppeteer

## :pencil:Requisitos

* **RAM**: 512 MB (recomendado para tarefas básicas)
  * A quantidade ideal de **RAM** pode variar consoante as especificidades de cada caso.

## :package:Adicione o puppetter no [APT](../../discloud.config/configurar/apt.md) do [discloud.config](broken-reference)

Na linha **APT**, adicione o pacote `puppeteer` separado por vírgula e espaço após os pacotes já existentes, como no exemplo abaixo.

{% code title="discloud.config" %}
```typescript
...
APT=tools, puppeteer
...
```
{% endcode %}

## :gear:Configure o Puppetter

Para garantir o funcionamento correto do **Puppeteer** em um container, é necessário adicionar o argumento `--no-sandbox` na instrução `puppeteer.launch();`, como demonstrado no exemplo a seguir:

```javascript
const browser = await puppeteer.launch({
  args: ['--no-sandbox']
});
```

## <img src="https://wwebjs.dev/logo.png" alt="" data-size="line"> Configure o [whatsapp-web.js](https://wwebjs.dev/guide/#installation-on-no-gui-systems)

Como o whatsapp-web.js utiliza o **Puppetter**, é necessário adicionar o argumento `--no-sandbox` às opções do puppetter, como no exemplo a seguir:

```javascript
const client = new Client({
	puppeteer: {
		args: ['--no-sandbox'],
	}
});
```

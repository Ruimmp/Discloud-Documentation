# 🏗 VERSION (Alterne entre Versões)

Altere a versão da linguagem da sua aplicação sempre que necessário, seja da mais antiga à mais recente.

## :gear: Como Utilizar

Consulte as [versões disponíveis](version.md#versoes-disponiveis) conforme a linguagem da sua app, e coloque em `VERSION=`

{% code title="discloud.config" %}
```typescript
...
VERSION=current
...
```
{% endcode %}

> Observação: Os `...` apenas indicam continuidade de outras opções anteriores ou posteriores à linha VERSION, que não são revelantes e mencionados nesta página.

### Versões disponíveis

> Selecione uma linguagem para consultar

{% tabs %}
{% tab title=" 🟨 JavaScript" %}
<table><thead><tr><th>Versões Disponíveis</th><th data-hidden></th></tr></thead><tbody><tr><td><a data-footnote-ref href="#user-content-fn-1">latest</a></td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-2">current</a></td><td></td></tr><tr><td>16.13.2</td><td></td></tr><tr><td>14.18.3</td><td></td></tr><tr><td><a data-footnote-ref href="#user-content-fn-3">suja</a></td><td></td></tr></tbody></table>
{% endtab %}

{% tab title="🐍 Python" %}
| Versões Disponíveis |
| ------------------- |
| latest[^4]          |
| 3.10                |
| 3.9.10              |
| 2.7.18              |
| suja                |
{% endtab %}

{% tab title="☕ Java" %}
| Versões Disponíveis |
| ------------------- |
| latest[^5]          |
| 18.x.x              |
| 17.x.x              |
| 16.x.x              |
{% endtab %}

{% tab title="💎 Ruby" %}
| Versões Disponíveis |
| ------------------- |
| latest[^6]          |
| 3.1.0               |
| 2.7.5               |
{% endtab %}

{% tab title="🐿️ Go" %}
| Versões Disponíveis |
| ------------------- |
| latest[^7]          |
| 1.17.6              |
| 1.16.13             |
{% endtab %}

{% tab title="🐘 Php" %}
| Versões Disponíveis |
| ------------------- |
| latest[^8]          |
{% endtab %}

{% tab title="🦀 Rust" %}
| Versões Disponíveis |
| ------------------- |
| latest[^9]          |
| suja                |
{% endtab %}
{% endtabs %}





[^1]: Versão **estável** mais recente do Node.js disponível (**LTS**) <mark style="color:green;">(recomendado)</mark>

[^2]: versão mais recente do Node.js disponível

[^3]: A versão **suja** é a versão "latest", mas é mais pesada devido ao grande número de pacotes [APT](apt.md#pacotes-disponiveis) já pré-instalados, incluindo pacotes não estão listados. \
    \
    No entanto, recomendamos usá-la apenas como último recurso. A maioria das aplicações não precisa desta versão. \
    \
    Se necessitar de um pacote específico, consulte nossa [lista de pacotes APT](apt.md#pacotes-disponiveis) e instale-o individualmente, se o pacote pretendido não estiver disponível, por favor contacte o suporte para adicionar

[^4]: Versão **estável** mais recente do **Python** <mark style="color:green;">(recomendado)</mark>

[^5]: Versão **estável** mais recente do **Openjdk**

[^6]: Versão **estável** mais recente do **Ruby** <mark style="color:green;">(recomendado)</mark>

[^7]: versão mais recente do **Go** <mark style="color:green;">(recomendado)</mark>

[^8]: versão mais recente do **Php** <mark style="color:green;">(recomendado)</mark>

[^9]: versão mais recente do **Rust** <mark style="color:green;">(recomendado)</mark>

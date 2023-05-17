---
cover: ../.gitbook/assets/api-banner.png
coverY: 683.9595959595961
---

# 📡 Usar a API

## :pencil: Requisitos

#### Obter o token

Para obter o seu token use o comando [api](../suporte/comandos/api.md).

<figure><img src="../.gitbook/assets/api-cmd.png" alt=""><figcaption></figcaption></figure>

## Começar

[Acesse as rotas da API](https://discloud.github.io/apidoc/)\
Clique em `Authorize` e cole o seu Token da API

<figure><img src="../.gitbook/assets/api-login.png" alt=""><figcaption><p>Colocando o token</p></figcaption></figure>

## Comece a usar a API

exemplo com a rota `/user`

<figure><img src="../.gitbook/assets/api-getuser-example.png" alt=""><figcaption><p>Exemplo da responta da rota /user</p></figcaption></figure>

Você pode importar o código `curl` em aplicativos como o [Insomnia](https://insomnia.rest/download) ou [Postman](https://www.postman.com/downloads/), e a partir deles gerar o código para a linguagem que desejar

> Exemplos:

{% tabs %}
{% tab title="Insomnia" %}
<div align="left">

<figure><img src="../.gitbook/assets/insomnia-generate-code.png" alt=""><figcaption><p>1</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/insomnia-code.png" alt=""><figcaption><p>2</p></figcaption></figure>

</div>


{% endtab %}

{% tab title="Postman" %}
<div align="left">

<figure><img src="../.gitbook/assets/postman-generate-code.png" alt=""><figcaption><p>1</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/postman-code.png" alt=""><figcaption><p>2</p></figcaption></figure>

</div>
{% endtab %}
{% endtabs %}

Exemplo com a rota `/upload`

* O seu arquivo `.zip` deve incluir o [discloud.config](../discloud.config/configurar/)
* O seu arquivo `.zip` deve ter um tamanho `<=100MB`

<figure><img src="../.gitbook/assets/api-upload-example.png" alt=""><figcaption></figcaption></figure>

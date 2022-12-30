---
cover: ../.gitbook/assets/api-banner.png
coverY: 683.9595959595961
---

# 📡 Usar a API

## :pencil: Requisitos

#### Obter o token

Para obter o seu token use o comando [api](../suporte/comandos/api.md).

## Começar

<figure><img src="../.gitbook/assets/insomnia-discloudapi-user.png" alt=""><figcaption></figcaption></figure>

### Comece a usar a API

{% code title="Shell" %}
```shell
curl --request GET \
  --url https://api.discloud.app/v2/user \
  --header 'api-token: DISCLOUD_TOKEN'
```
{% endcode %}

{% hint style="info" %}
Renomeie `DISCLOUD_TOKEN` com o seu token
{% endhint %}

Você pode importar o código a cima em aplicativos como o [Insomnia](https://insomnia.rest/download) ou [Postman](https://www.postman.com/downloads/), e a partir deles testar e gerar códigos para a linguagem que desejar

> Exemplos:

{% tabs %}
{% tab title="Insomnia" %}
<div>

<figure><img src="../.gitbook/assets/insomnia-generate-code.png" alt=""><figcaption><p>1</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/insomnia-code.png" alt=""><figcaption><p>2</p></figcaption></figure>

</div>


{% endtab %}

{% tab title="Postman" %}
<div>

<figure><img src="../.gitbook/assets/postman-generate-code.png" alt=""><figcaption><p>1</p></figcaption></figure>

 

<figure><img src="../.gitbook/assets/postman-code.png" alt=""><figcaption><p>2</p></figcaption></figure>

</div>
{% endtab %}
{% endtabs %}

## Fazer o upload de um projeto com a API

### :pencil:Requisitos

* O seu arquivo `.zip` deve incluir o [discloud.config](../discloud.config/configurar/)
* O seu arquivo `.zip` deve ter um tamanho `<=100MB`

<figure><img src="../.gitbook/assets/discloud-api-up.png" alt=""><figcaption></figcaption></figure>

{% code title="Shell" %}
```shell
curl --request POST \
  --url https://api.discloud.app/v2/upload \
  --header 'Content-Type: multipart/form-data' \
  --header 'api-token: DISCLOUD_TOKEN' \
  --header 'content-type: multipart/form-data; boundary=---011000010111000001101001' \
  --form file=@/home/diogo/Documents/bot/Archive.zip
```
{% endcode %}

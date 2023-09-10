---
description: >-
  Não sabe como hospedar a sua aplicação no nosso Painel de Controle? Veja as
  instruções abaixo!
---

# ☁ Como Hospedar

## :bust\_in\_silhouette: Faça seu registro em nosso site

Para realizar o seu registro na [**Discloud**](https://discloudbot.com/login), clique em [entrar](https://discloudbot.com/login) e logo depois faça o ‘login’ através da sua conta [Github](https://github.com/).

<figure><img src="../../.gitbook/assets/discloud-dash-login.png" alt=""><figcaption></figcaption></figure>

## 2- Acesse o seu painel de controle

<figure><img src="../../.gitbook/assets/image (1) (3).png" alt=""><figcaption><p>Acesse o painel de controle após o seu login no site</p></figcaption></figure>

## 3- Clique no botão para hospedar sua aplicação

<figure><img src="../../.gitbook/assets/3.png" alt=""><figcaption><p>Clique no botão indicado para hospedar uma nova aplicação</p></figcaption></figure>

## 4- Crie um arquivo .zip

> **Remova (ou não inclua no .zip) as seguintes pastas/arquivos** nos seguintes projetos:\
> :yellow\_square:[JavaScript](../linguagens/javascript/): remova `node_modules`, `.npm` e `package-lock.json`\
> :snake:[Python](../linguagens/python/): remova `venv` e `.cache`

{% content-ref url="../linguagens/" %}
[linguagens](../linguagens/)
{% endcontent-ref %}

{% hint style="danger" %}
**Coloque o arquivo** [discloud.config](../../discloud.config/configurar/#exemplo-para-bot) na raiz do seu projeto e não se esqueça de incluir no .zip\
\
Sem esse arquivo seu upload não vai funcionar!!
{% endhint %}

{% content-ref url="../../discloud.config/configurar/" %}
[configurar](../../discloud.config/configurar/)
{% endcontent-ref %}

## :cloud:Hospedar os seus Apps

{% hint style="info" %}
Para hospedar sites consulte os [requisitos](sites/#requisitos)
{% endhint %}

<figure><img src="../../.gitbook/assets/dash-drop-file.png" alt=""><figcaption><p>Arraste o .zip com o seu projeto</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/dash-send-zip.png" alt=""><figcaption></figcaption></figure>

## :link:Outros Métodos

:robot:Para Bots:

> * :electric\_plug:[via Bot](bots/bot.md)
> * :jigsaw:[via VSCode](bots/vscode.md)
> * :keyboard:[via DisCloud CLI](bots/cli.md)

:earth\_americas:Para Sites:

> * :electric\_plug:[via Bot](sites/bot.md)
> * :jigsaw:[via VSCode](sites/vscode.md)
> * :keyboard:[via DisCloud CLI](sites/cli.md)

---
description: >-
  Não sabe como hospedar a sua aplicação no nosso Painel de Controle? Veja as
  instruções abaixo!
---

# ☁ Como Hospedar

## :bust\_in\_silhouette:Registro

Para realizar o seu registro na [**Discloud**](https://discloudbot.com/login), faça o ‘login’ através da sua conta [Github](https://github.com/).

<figure><img src="../../.gitbook/assets/discloud-dash-login.png" alt=""><figcaption></figcaption></figure>

## <img src="../../.gitbook/assets/DiscordLogo1.png" alt="" data-size="line">Integrar com uma conta Discord (opcional)

{% hint style="info" %}
Não é possível criar **novos registros** usando uma conta Discord. No entanto, você pode integrá-la a uma conta Github para importar seu plano atual e aplicativos existentes.
{% endhint %}

Para importar o seu **plano atual** e **aplicativos** já hospedados, siga as instruções abaixo.

<figure><img src="../../.gitbook/assets/discloud-dash-discord-integration.png" alt=""><figcaption><p>Clique no aviso em amarelo para integrar a sua conta Discord</p></figcaption></figure>

## :cloud:Hospedar as suas apps

{% content-ref url="../linguagens/" %}
[linguagens](../linguagens/)
{% endcontent-ref %}

> 1. **Remova (ou não inclua no .zip) as seguintes pastas/arquivos** nos seguintes projetos:\
>    :yellow\_square:[JavaScript](../linguagens/javascript/): remova `node_modules`, `.npm` e `package-lock.json`\
>    :snake:[Python](../linguagens/python/): remova `venv` e `.cache`\
>    ``outros: `.git`
> 2. **Coloque o arquivo** [discloud.config](broken-reference) na raiz do seu projeto e não se esqueça de incluir no .zip

<figure><img src="../../.gitbook/assets/dash-drop-file.png" alt=""><figcaption><p>Arraste o .zip com o seu projeto</p></figcaption></figure>

<figure><img src="../../.gitbook/assets/dash-send-zip.png" alt=""><figcaption></figcaption></figure>

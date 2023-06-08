---
description: Saiba como configurar um domínio personalizado com um app na Discloud
---

# 🌐 Seu próprio domínio

<figure><img src="../../.gitbook/assets/Discloud-domain.png" alt=""><figcaption><p>Como o domínio funciona na Discloud</p></figcaption></figure>

## :pencil:Requisitos

Para começar a utilizar o seu domínio na **Discloud**, tem de cumprir os seguintes requisitos:

1. É necessário um [Plano Diamante](https://discloudbot.com/plans) **ou superior**.
2. É necessário ter uma aplicação que utilize um **subdomínio**, é necessário para estabelecer uma ligação ao seu **nome de domínio**.
3. Além disso, já deve ter um **nome de domínio** :)

## :globe\_with\_meridians:Adicionar o seu domínio <a href="#add-your-domain" id="add-your-domain"></a>

1. Em seu navegador, faça login na [Dashboard da DIscloud](https://discloudbot.com/dashboard) e selecione **Custom Domain**
2. Digite seu **nome de domínio**, selecione o **subdomínio** desejado, e clique em <mark style="background-color:green;">Registrar</mark>

<figure><img src="../../.gitbook/assets/dash-custom-domain.png" alt=""><figcaption></figcaption></figure>

## :white\_check\_mark:Verifique o seu domínio

A primeira coisa que tem de fazer depois de adicionar um nome de domínio personalizado é mostrar à **Discloud** que você controla este domínio.

Isso pode ser feito adicionando registros TXT com um código exclusivo gerado pela **Discloud**, aos registros de DNS do seu domínio (no portal de gerenciamento de domínios do seu registrador)

{% hint style="info" %}
Nestas docs, focamos apenas na configuração com a **Cloudflare**.
{% endhint %}

### <img src="../../.gitbook/assets/cloudflare-logo.png" alt="" data-size="line">Cloudflare <a href="#activate-your-domain" id="activate-your-domain"></a>

Faça login na sua [conta Cloudflare](https://dash.cloudflare.com) e selecione o domínio que deseja usar.

<figure><img src="../../.gitbook/assets/cloudflare-domain.png" alt=""><figcaption></figcaption></figure>

Selecione a guia **DNS** → **Adicionar registro**. Digite os seguintes valores:

> * **Type**: CNAME
> * **Name**: @ (Se o valor @ não for aceite, digite seu domínio em vez disso)
> * **Target**: hosting.discloud.app

<figure><img src="../../.gitbook/assets/domain-cloudflare-cname.png" alt=""><figcaption><p>Exemplo com os valores adicionados</p></figcaption></figure>

Vá para a janela de **Configuração de domínio** na Discloud. Cole o texto que você copiou de **Name** / **Value** e cole-o num registro na **Cloudflare**, faça o mesmo com as **2 linhas TXT**.

<div>

<figure><img src="../../.gitbook/assets/set-up-your-domain-window.png" alt=""><figcaption><p>Janela de configuração do domínio personalizado do Discloud.</p></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/domain-cloudflare-records.png" alt=""><figcaption><p>Como devem ser colados no registro do Cloudflare</p></figcaption></figure>

</div>

#### Resultado esperado

<figure><img src="../../.gitbook/assets/cloudflare-domain-result.png" alt=""><figcaption></figcaption></figure>

## :construction\_site:Reconstrua o seu app

Selecione o app que pertence ao seu domínio e clique em **Rebuild**

<div>

<figure><img src="../../.gitbook/assets/dash-select-domain-app.png" alt=""><figcaption></figcaption></figure>

 

<figure><img src="../../.gitbook/assets/dash-rebuild-app.png" alt=""><figcaption></figcaption></figure>

</div>

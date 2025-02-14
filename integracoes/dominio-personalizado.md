# 🌐 Domínio Personalizado

## 🌐 Seu Próprio Domínio na Discloud

Ao utilizar a **Discloud**, é possível configurar um domínio personalizado para seus aplicativos hospedados. Isso permite que você tenha um endereço próprio, como **meudominio.com**, em vez de um subdomínio padrão da Discloud.

<figure><img src="../.gitbook/assets/custom-domain-flow.png" alt=""><figcaption><p>Como o domínio funciona na Discloud</p></figcaption></figure>

***

## 📋 Requisitos para Usar um Domínio Personalizado

Para configurar o seu domínio personalizado na Discloud, você precisará:

<table data-view="cards"><thead><tr><th align="center"></th><th></th></tr></thead><tbody><tr><td align="center"><strong>Plano Platinum ou Superior</strong></td><td>Necessário para habilitar o subdomínio. Confira nossos <a href="https://discloud.com/plans">planos</a>.</td></tr><tr><td align="center"><strong>App com Subdomínio</strong></td><td>O app já deve utilizar um subdomínio <strong>.discloud.app</strong> para vinculação com o seu domínio.</td></tr><tr><td align="center"><strong>Domínio Próprio</strong></td><td>Já deve possuir um domínio registrado. Sugerimos <a href="https://www.cloudflare.com/products/registrar/">Cloudflare</a>, <a href="https://www.godaddy.com/">GoDaddy</a>, <a href="https://registro.br/">Registro.br</a>, ou <a href="https://www.namecheap.com/">Namecheap</a>.</td></tr></tbody></table>

***

## 🌍 Como Adicionar Seu Domínio

{% stepper %}
{% step %}
**Acesse a** [**Dashboard da Discloud**](https://discloud.com/dashboard) **e selecione Domínio Personalizado.**
{% endstep %}

{% step %}
**Insira o seu domínio e escolha o subdomínio desejado. Depois, clique em Registrar.**

<img src="../.gitbook/assets/dashboard-custom-domain.png" alt="Registro de domínio personalizado na dashboard" data-size="original">
{% endstep %}
{% endstepper %}

***

## ✅ Verificando Seu Domínio

Após registrar o domínio, você precisa provar à Discloud que é o proprietário do domínio, adicionando **registros TXT** no DNS do seu domínio, fornecidos pela Discloud.

{% hint style="info" %}
**Configuração de DNS com Cloudflare**\
\
Nesta documentação focamos na configuração com **Cloudflare** como exemplo devido a sua praticidade.&#x20;
{% endhint %}

***

### Configuração do Cloudflare

{% stepper %}
{% step %}
**Faça login na** [**Cloudflare**](https://dash.cloudflare.com) **e selecione o domínio desejado.**
{% endstep %}

{% step %}
**Vá até a guia DNS e adicione um novo registro com os seguintes valores:**

* **Type**: CNAME&#x20;
* **Name**: @ ou o seu domínio&#x20;
* **Target**: hosting.discloud.app

<img src="../.gitbook/assets/cloudflare-domain-cname.png" alt="Exemplo de configuração CNAME no Cloudflare" data-size="original">
{% endstep %}

{% step %}
**Verificação TXT**

Na **Dashboard Discloud**, copie o código **TXT** fornecido e adicione-o na configuração DNS do Cloudflare.

{% hint style="info" %}
Caso o valor TXT retorne como `null`, isso indica que a Cloudflare (CF) já realizou a validação do domínio. Nesse caso, não é necessário inserir o registro TXT novamente.
{% endhint %}

<img src="../.gitbook/assets/dashboard-domain-txt-setup.png" alt="Código TXT para verificação do domínio" data-size="original">

<img src="../.gitbook/assets/cloudflare-txt-record.png" alt="Configuração do registro TXT no Cloudflare" data-size="original">
{% endstep %}
{% endstepper %}

***

## 🌐 Usando Subdomínios com Seu Domínio

Se você optou por adicionar um subdomínio ao seu domínio para uso na Discloud, a Cloudflare exibirá os valores de "name" configurados com o nome do subdomínio. Por exemplo, se você criou um subdomínio chamado **dash.seudominio.com**, o resultado ficará assim:

<figure><img src="../.gitbook/assets/cloudflare-subdomain-setup-result.png" alt=""><figcaption><p>Resultado esperado para subdomínio no Cloudflare</p></figcaption></figure>

***

## 🔄 Reconstruindo seu App

Após verificar o domínio, selecione o app que pertence ao domínio e clique em **Rebuild** para aplicar as mudanças.

<figure><img src="../.gitbook/assets/dashboard-rebuild-app.png" alt=""><figcaption><p>Reconstrução do app para aplicar o domínio</p></figcaption></figure>

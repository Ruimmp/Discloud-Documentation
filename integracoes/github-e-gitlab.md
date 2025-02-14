# 🐙 GitHub e GitLab

## 📝 Requisitos

Para iniciar a configuração de sincronização do seu repositório GitLab ou GitHub com a Discloud, é necessário que você tenha uma aplicação previamente configurada na plataforma e um repositório disponível no GitLab ou GitHub. Esta integração permite automatizar o processo de deploy de suas aplicações, garantindo que quaisquer atualizações no código sejam refletidas automaticamente em seu ambiente de hospedagem. Siga os passos abaixo para configurar sua sincronização e simplificar o gerenciamento contínuo de suas aplicações na nuvem.

***

## 🚀 Passos para Configuração

{% hint style="info" %}
**Informação Importante**\
\
No momento, a configuração de sincronização só pode ser iniciada via comando `.git` no canal [**#🔌・commands**](https://discord.com/channels/584490943034425391/1051126795883261962) no Discord.
{% endhint %}

{% tabs %}
{% tab title="GitHub" %}
{% stepper %}
{% step %}
**Após usar o comando `.git`, você receberá uma mensagem privada com instruções.**

![Mensagem privada no Discord](../.gitbook/assets/github-private-message.png)
{% endstep %}

{% step %}
**Siga as instruções no seu privado com o bot para configurar o webhook no GitHub fornecendo o link do repositório.**

<img src="../.gitbook/assets/discord-webhook-instructions.png" alt="Instruções de Webhook no Discord" data-size="original">
{% endstep %}

{% step %}
**Ao enviar o link do repositório, se acessível, você receberá os dados necessários para configurar o webhook.**

{% hint style="info" %}
**Token de Acesso Pessoal**\
\
Caso o seu repositório seja privado ou não seja acessível, você precisará fornecer um token de acesso pessoal. Siga as instruções de como criar um token de acesso pessoal em [Configuração de Token](github-e-gitlab.md#configuracao-de-token).
{% endhint %}

<img src="../.gitbook/assets/github-webhook-config.png" alt="Dados de Webhook GitHub" data-size="original">
{% endstep %}

{% step %}
**Acesse as configurações do repositório no GitHub e adicione o webhook fornecido.**

<img src="../.gitbook/assets/webhook-setup-example-2.png" alt="Outro exemplo de Webhook" data-size="original">
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="GitLab" %}
{% hint style="info" %}
**Em Breve**\
\
A integração com o GitLab estará disponível em breve. Fique atento às atualizações.
{% endhint %}
{% endtab %}
{% endtabs %}

***

## 🔐 Configuração de Token

Você precisará de um token de acesso pessoal para permitir a integração. Siga as instruções no link abaixo:

{% embed url="https://github.com/settings/tokens" %}
Acessar Configurações de Token
{% endembed %}

<figure><img src="../.gitbook/assets/github-token-setup.gif" alt=""><figcaption><p>Configuração de Token no GitHub</p></figcaption></figure>

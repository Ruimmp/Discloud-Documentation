---
description: >-
  Aprenda a hospedar rapidamente suas aplicações através do nosso servidor Discord usando
  nosso bot.
icon: robot
---

# Bot do Discord

A Discloud permite que você **hospede aplicações diretamente do Discord**, tornando a implantação rápida e acessível sem precisar usar um painel ou ferramentas de linha de comando.

***

## 🔑 Verificação de Conta

Antes de implantar aplicações usando o **Bot da Discloud**, você deve primeiro **verificar sua conta** no servidor Discord da Discloud.

### **🤔 Como Verificar Sua Conta:**

{% stepper %}
{% step %}
Entre no [**Servidor Discord da Discloud**](https://discord.discloudbot.com/).
{% endstep %}

{% step %}
Siga as instruções no canal de verificação.

<figure><img src="../.gitbook/assets/Discord-Verify_Channel.png" alt=""><figcaption></figcaption></figure>
{% endstep %}

{% step %}
Uma vez verificado, você receberá o cargo **`Verified en-us`**.
{% endstep %}
{% endstepper %}

{% hint style="info" %}
Após a verificação, você ganhará acesso ao canal [**`#🔌・commands`**](https://discord.com/channels/584490943034425391/1051126795883261962), onde poderá gerenciar suas aplicações.
{% endhint %}

***

## 🚀 Hospedando Sua Aplicação

Há **duas maneiras** de implantar uma aplicação usando o Bot da Discloud:

<table><thead><tr><th width="212">Método</th><th>Melhor Para</th><th>Como Funciona</th></tr></thead><tbody><tr><td><a href="discord-bot.md#advanced-setup"><strong>⚙️ Configuração Avançada</strong></a></td><td>Usuários que querem uma <strong>implantação de um comando</strong> com configurações pré-definidas.</td><td>Configure tudo no arquivo <a href="../configurations/discloud.config/"><code>discloud.config</code></a> e use <code>.upconfig</code>.</td></tr><tr><td><a href="discord-bot.md#quick-setup-step-by-step-guide"><strong>⚡ Configuração Rápida (legado)</strong></a></td><td>Usuários que <strong>preferem uma configuração guiada</strong> através dos prompts do bot.</td><td>O bot perguntará os detalhes necessários após executar <code>.up</code>.</td></tr></tbody></table>

{% hint style="warning" %}
**Notas Importantes:**

* Se seu [**arquivo principal**](../faq/general-questions/wip-what-is-the-main-file.md) **não estiver no** [**diretório raiz**](../faq/general-questions/what-is-the-root-of-the-project.md), você **deve** usar Configuração Avançada ou movê-lo para a raiz.
* Se você estiver hospedando um **bot sem ID** (ex.: WhatsApp ou Telegram), use Configuração Avançada e a Discloud gerará o ID automaticamente.
{% endhint %}

{% tabs %}
{% tab title="📝 Configuração Avançada" %}
{% stepper %}
{% step %}
Crie o arquivo [`discloud.config`](../configurations/discloud.config/).
{% endstep %}

{% step %}
Comprima seu projeto em um arquivo [`.zip`](../faq/general-questions/wip-how-to-compress.md).
{% endstep %}

{% step %}
Faça upload do seu projeto.

* Vá para [**`#🔌・commands`**](https://discord.com/channels/584490943034425391/1051126795883261962) no **Servidor Discord da Discloud**.
*   Execute o seguinte comando:

    ```
    .upconfig
    ```
* Envie seu arquivo [**.zip**](../faq/general-questions/wip-how-to-compress.md) quando solicitado.
{% endstep %}

{% step %}
Sua aplicação será implantada automaticamente.
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="⚡ Configuração Rápida (Guia Passo a Passo)" %}
{% tabs %}
{% tab title="🤖 Bot" %}
{% stepper %}
{% step %}
Prepare seu projeto.

* Certifique-se de que os arquivos da sua aplicação estejam estruturados corretamente.
* Comprima seu projeto em um arquivo [`.zip`](../faq/general-questions/wip-how-to-compress.md).
{% endstep %}

{% step %}
Faça upload do seu projeto.

* Vá para [**`#🔌・commands`**](https://discord.com/channels/584490943034425391/1051126795883261962) no **Servidor Discord da Discloud**.
*   Execute o seguinte comando:

    ```
    .up
    ```
{% endstep %}

{% step %}
**Forneça as Informações Necessárias.**

* **Digite o** [**ID da Aplicação**](../faq/general-questions/wip-how-can-i-get-my-bots-id.md) (para bots do Discord).
* **Digite o** [**Nome do Arquivo Principal**](../faq/general-questions/wip-what-is-the-main-file.md) (ex.: `index.js`, `main.py`, `main.go`).
*   **Especifique a RAM** para seu bot (ex.: `100` para 100MB).

    {% hint style="info" %}
    Ao especificar a quantidade de RAM, você não precisa incluir unidades como "MB". Basta inserir o valor numérico, por exemplo, "100" para 100MB.

    ```
               BOTs requerem um mínimo de 100MB de RAM.
    ```
    {% endhint %}
{% endstep %}

{% step %}
Envie seu arquivo [`.zip`](../faq/general-questions/wip-how-to-compress.md) quando solicitado.
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="🌐 Site" %}
{% stepper %}
{% step %}
Prepare seu projeto.

* Certifique-se de que os arquivos da sua aplicação estejam estruturados corretamente.
* Comprima seu projeto em um arquivo [`.zip`](../faq/general-questions/wip-how-to-compress.md).
{% endstep %}

{% step %}
Faça upload do seu projeto.

* Vá para [**`#🔌・commands`**](https://discord.com/channels/584490943034425391/1051126795883261962) no **Servidor Discord da Discloud**.
*   Execute o seguinte comando:

    ```
    .upsite
    ```
{% endstep %}

{% step %}
**Forneça as Informações Necessárias.**

* **Escolha um** [**Subdomínio**](../faq/general-questions/wip-how-to-create-a-subdomain.md).
* **Digite o** [**Nome do Arquivo Principal**](../faq/general-questions/wip-what-is-the-main-file.md) (ex.: `index.html`, `index.php`).
*   **Especifique a RAM** para seu bot (ex.: `512` para 512MB).

    {% hint style="info" %}
    Ao especificar a quantidade de RAM, você não precisa incluir unidades como "MB". Basta inserir o valor numérico, por exemplo, "512" para 512MB.

    ```
               Sites requerem um mínimo de 512MB de RAM.
    ```
    {% endhint %}
{% endstep %}

{% step %}
Envie seu arquivo [`.zip`](../faq/general-questions/wip-how-to-compress.md) quando solicitado.
{% endstep %}
{% endstepper %}
{% endtab %}
{% endtabs %}
{% endtab %}
{% endtabs %}

***

## **❓ Ainda precisa de ajuda?**

Verifique a [**Seção FAQ**](broken-reference) ou junte-se ao nosso [**Servidor Discord**](https://discord.discloudbot.com/) para suporte.
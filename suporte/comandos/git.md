# git

Sincronize um repositório git com a sua aplicação para atualizações _(commits)_ automáticas.

Sempre que um commit for enviado para o repositório da sua aplicação, a DisCloud irá atualizar os arquivos da sua aplicação automaticamente.

<figure><img src="../../.gitbook/assets/git-logs.png" alt=""><figcaption><p>Exemplo dos logs do git na DisCloud durante um deploy</p></figcaption></figure>

{% hint style="info" %}
Este recurso só está disponível para os planos pagos.
{% endhint %}

## :pencil: Requisitos

É necessário que a sua aplicação já esteja hospedada na DisCloud.

## **Como Usar?**

#### Entre no canal de texto `#🔌・commands` e digite `.git`

<div align="center">

<figure><img src="../../.gitbook/assets/git-cmd-discord.png" alt=""><figcaption><p>Comando .git no canal de comandos</p></figcaption></figure>

</div>

{% tabs %}
{% tab title="Github" %}
## URL do Repositório

Entre na DM do bot da DisCloud e cole a URL do repositório para a sua aplicação.

<figure><img src="../../.gitbook/assets/git-url.png" alt=""><figcaption><p>Colando o URL do repositorio</p></figcaption></figure>

## Configure o Token de Acesso ([Abrir Github](https://github.com/settings/personal-access-tokens/new))

É importante que o acesso esteja para todos os repositórios _(principalmente se você desejar ativar a sincronização para mais de 1 aplicação)_

<figure><img src="../../.gitbook/assets/github-fine-grained-token.png" alt=""><figcaption></figcaption></figure>

### Configuração de Permissões

Selecione a configuração de `Webhooks` para apenas leitura e gere o seu Token.

<figure><img src="../../.gitbook/assets/github-fine-grained-token-perms.png" alt=""><figcaption></figcaption></figure>

## Webhook

Abra o repositório da sua aplicação e crie um `webhook`

<figure><img src="../../.gitbook/assets/github-addwebhook.png" alt=""><figcaption></figcaption></figure>

### Configurando o Webhook

Certifique-se de mudar o `content type` para `application/json`

<figure><img src="../../.gitbook/assets/github-webhook.png" alt=""><figcaption></figcaption></figure>
{% endtab %}
{% endtabs %}




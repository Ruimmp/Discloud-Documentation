---
description: Guia passo a passo para hospedar o Lavalink na Discloud e configurar seu bot.
---

# 🎧 Lavalink

## 📝 Requisitos

Para sincronizar seu repositório GitLab ou GitHub com a Discloud, você precisará de:

* Uma aplicação configurada na Discloud.
* Um domínio ou subdomínio. A Discloud oferece subdomínios a partir do plano **Platinum** para usuários pagos.

***

## 🚀 Passos para Configuração do Lavalink

{% stepper %}
{% step %}
**Baixe o arquivo Lavalink.jar de** [**Lavalink Releases**](https://github.com/freyacodes/Lavalink/releases)**.**
{% endstep %}

{% step %}
**Configure o arquivo `application.yml`:**

* Altere a porta para `8080`.
* Configure uma senha de acesso.

{% embed url="https://github.com/lavalink-devs/Lavalink/blob/master/LavalinkServer/application.yml.example" %}
Documentação Lavalink - Exemplo de Configuração
{% endembed %}
{% endstep %}

{% step %}
**Crie um** [**`discloud.config`**](../configuracoes/discloud-config.md) **com as configurações do ambiente.**
{% endstep %}

{% step %}
**Compacte os três arquivos (`Lavalink.jar`, `application.yml`, e `discloud.config`) em um** [**`.zip`**](../ajuda-e-suporte/suporte-tecnico/faq/compactar-projeto.md)**.**
{% endstep %}
{% endstepper %}

***

## ⚙️ Configuração do Bot com Lavalink

Quando o Lavalink estiver rodando, configure o bot com os seguintes parâmetros:

```json
{
  "host": "exemplo.discloud.app",
  "port": 443,
  "secure": true,
  "password": "youshallnotpass"
}
```

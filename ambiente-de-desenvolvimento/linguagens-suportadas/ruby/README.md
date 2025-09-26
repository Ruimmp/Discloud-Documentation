---
description: Guia completo para hospedar aplicações Ruby no Discloud.
icon: gem
---

# Ruby

## 📁 **Preparando os Arquivos**

Antes de fazer upload do seu projeto, você deve **excluir arquivos desnecessários** para otimizar o deploy.

#### ❌ **Arquivos a Excluir**

Certifique-se de que os seguintes arquivos e diretórios **não** sejam incluídos no seu [`.zip`](../../../faq/perguntas-gerais/em-andamento-como-comprimir.md):

```diff
- Gemfile.lock
- .git
- tmp/
- log/
```

📌 **Use um arquivo** [**`.discloudignore`**](../../../configuracoes/.discloudignore.md) **para excluir automaticamente esses arquivos.**

🔗 **Precisa de ajuda para configurar seu** [**`Gemfile`**](gemfile.md) **ou encontrar o** [**arquivo principal**](../../../faq/perguntas-gerais/em-andamento-qual-e-o-arquivo-principal.md)**?**

***

### 🌐 Hospedando Seu Site com Ruby on Rails

Antes de fazer deploy do seu website ou API no Discloud, certifique-se de que você atenda aos seguintes **requisitos**:

{% hint style="success" %}
[Plano Platinum ou superior](https://discloud.com/plans) é necessário para hospedar websites ou APIs.
{% endhint %}

{% hint style="success" %}
[Um subdomínio deve ser criado](../../../faq/perguntas-gerais/em-andamento-como-criar-um-subdominio.md) antes do deploy.
{% endhint %}

{% hint style="danger" %}
Porta `8080` é obrigatória – As aplicações devem escutar nesta porta.
{% endhint %}

### ⚙️ Configurando Ruby on Rails

{% code title="config/application.rb" %}
```ruby
require_relative "boot"

require "rails/all"

# Requer as gems listadas no Gemfile, incluindo aquelas limitadas a :test, :development ou :production.
Bundler.require(*Rails.groups)

module RailsOnDiscloud
  class Application < Rails::Application
    # Inicializa a configuração padrão para a versão originalmente gerada do Rails.
    config.load_defaults 7.0
    # config.time_zone = "Central Time (US & Canada)"
    # config.eager_load_paths << Rails.root.join("extras")
    Rails.application.config.hosts = [
      IPAddr.new("0.0.0.0/0"),        # Todos os endereços IPv4.
      IPAddr.new("::/0"),             # Todos os endereços IPv6.
      "localhost",                    # Domínio reservado localhost.
      "seusubdomínio.discloud.app"    # !!! Subdomínio Discloud !!!
    ]
  end
end
```
{% endcode %}

***

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** no Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../como-hospedar-usando/painel-de-controle.md">painel-de-controle.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/bot-do-discord.md">bot-do-discord.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord do Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

# 📄 Criar o Gemfile

Um arquivo `Gemfile` descreve as dependências **gem** necessárias para executar o seu projeto.

### Como criar o arquivo `Gemfile`?

Abra o Terminal no diretório do seu projeto (Windows use: **Shift+Botão Direito** e clique em **Open PowerShell**) e digite:

```
bundle init
```

![ Abrir o Terminal](../../../.gitbook/assets/ruby-open-terminal.png) ![Executando o comando](../../../.gitbook/assets/ruby-bundle-init.png)

{% hint style="info" %}
Você precisa do **Ruby** instalado no seu computador, caso não esteja instalado siga as instruções abaixo.
{% endhint %}

{% content-ref url="../../../ambiente-local/instalar/ruby.md" %}
[ruby.md](../../../ambiente-local/instalar/ruby.md)
{% endcontent-ref %}

### Colocando dependências no seu `Gemfile`

![Exemplo](../../../.gitbook/assets/ruby-example.png)

### [discordrb](https://rubygems.org/gems/discordrb) (rubygems)

Adicione a seguinte linha no seu `Gemfile`

{% code title="Gemfile" %}
```ruby
source "https://rubygems.org"
gem "discordrb"
```
{% endcode %}

### [discordrb](https://github.com/shardlab/discordrb) (github)

{% hint style="warning" %}
Se você quiser executar a versão mais recente do **`discordrb`**, fornece funcionalidades mais recentes, mas pode apresentar instabilidades.
{% endhint %}

{% code title="Gemfile" %}
```ruby
source "https://rubygems.org"
gem 'discordrb', github: 'shardlab/discordrb', branch: 'main'
```
{% endcode %}

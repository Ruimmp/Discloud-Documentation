---
description: Guia completo para hospedar aplicações PHP na Discloud.
icon: php
---

# Php

## 📁 **Preparando os Arquivos do Seu Projeto**

Se seu projeto usa Composer, certifique-se de que um [`composer.json`](composer.json.md) válido esteja na **raiz** do arquivo que você faz upload. A Discloud instalará as dependências automaticamente quando detectar este arquivo.

#### ❌ **Arquivos / Diretórios a Excluir**

Exclua itens que não são necessários para execução:

```diff
- vendor/
- node_modules/
- .git/
- tests/
- .cache/
```

📌 Use um arquivo [**`.discloudignore`**](../../../configuracoes/.discloudignore.md) para excluir diretórios que você **não** quer empacotar (ex.: `vendor/` se você preferir uma instalação limpa).

{% hint style="info" %}
Inclua `vendor/` APENAS se: você tem bibliotecas corrigidas localmente ou depende de extensões ou binários compilados durante a instalação que devem corresponder ao seu ambiente de desenvolvimento. Caso contrário, excluí-lo mantém os uploads menores e permite que a Discloud faça uma instalação fresca e reprodutível.
{% endhint %}

🔗 **Precisa de ajuda para encontrar o** [**arquivo principal**](../../../faq/perguntas-gerais/em-andamento-qual-e-o-arquivo-principal.md)**?**

---

## 📦 **Essenciais do composer.json**

Exemplo mínimo:

```json
{
  "name": "example/app",
  "type": "project",
  "require": {
    "guzzlehttp/guzzle": "^7.9"
  },
  "autoload": {
    "psr-4": {
      "App\\": "src/"
    }
  },
  "scripts": {
    "start": "php -S 0.0.0.0:8080 -t public"
  }
}
```

Após editar dependências localmente:

```bash
composer install
composer dump-autoload --optimize
```

Mais detalhes: [`composer.json`](composer.json.md)

---

## 🌐 **Hospedando Websites & APIs**

Antes de fazer deploy do seu website ou API na Discloud, certifique-se de que você atenda aos seguintes **requisitos**:

{% hint style="success" %}
[Plano Platinum ou superior](https://discloud.com/plans) é necessário para hospedar websites ou APIs.
{% endhint %}

{% hint style="success" %}
[Um subdomínio deve ser criado](../../../faq/perguntas-gerais/em-andamento-como-criar-um-subdominio.md) antes do deploy.
{% endhint %}

{% hint style="danger" %}
Porta `8080` é obrigatória – As aplicações devem escutar nesta porta.
{% endhint %}

{% tabs %}
{% tab title="Servidor Integrado" %}
Execute localmente / deploy simples:

```bash
php -S 0.0.0.0:8080 -t public
```

`public/index.php` mínimo:

```php
<?php
declare(strict_types=1);
echo "Olá, Discloud!";
```

{% endtab %}

{% tab title="Roteador Básico" %}
`public/index.php`:

```php
<?php
declare(strict_types=1);
$path = parse_url($_SERVER['REQUEST_URI'], PHP_URL_PATH);
header('Content-Type: application/json');
if ($path === '/status') {
    echo json_encode(['ok' => true]);
    return;
}
echo json_encode(['message' => 'Olá, Discloud!']);
```

{% endtab %}

{% tab title="Script do Composer" %}
Adicione ao `composer.json`:

```json
{
  "scripts": { "start": "php -S 0.0.0.0:8080 -t public" }
}
```

Execute:

```bash
composer run-script start
```

{% endtab %}
{% endtabs %}

---

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** na Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../como-hospedar-usando/painel-de-controle.md">painel-de-controle.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/bot-do-discord.md">bot-do-discord.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord da Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

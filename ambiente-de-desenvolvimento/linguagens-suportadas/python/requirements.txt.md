---
description: >-
  Aprenda como gerar e configurar o arquivo requirements.txt para definir
  dependências essenciais para hospedar seu projeto Python no Discloud.
---

# requirements.txt

## **🗂️ O que é `requirements.txt`?**

O arquivo `requirements.txt` é essencial para projetos Python. Ele lista todas as dependências e suas versões, garantindo instalação consistente de pacotes durante o deploy no Discloud.

***

## **🛠️ Como Criar `requirements.txt`**

Você pode criar este arquivo usando dois métodos:

{% tabs %}
{% tab title="Criação Manual" %}
{% stepper %}
{% step %}
**Crie um novo arquivo de texto no diretório do seu projeto.**
{% endstep %}

{% step %}
**Nomeie-o exatamente como `requirements.txt`.**
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="Geração Automática" %}
{% stepper %}
{% step %}
**Certifique-se de que Python e pip estão instalados (**[**guia de instalação**](../../local-environment/python.md)**).**
{% endstep %}

{% step %}
**Abra seu terminal no diretório do projeto e execute.**

```bash
pip freeze --user > requirements.txt
```

Isso gera automaticamente uma lista de todos os pacotes instalados com suas versões exatas.
{% endstep %}
{% endstepper %}
{% endtab %}
{% endtabs %}

***

## **📝** Estrutura do `requirements.txt`&#x20;

Seu arquivo deve seguir estes padrões:

*   **Pacote Básico (**[**Última Versão**](https://pypi.org/project/discord.py/#history)**)**

    ```
    discord.py
    ```
*   **Pacote com Versão Específica**

    ```
    discord.py==2.0.0
    ```
*   **Intervalo de Versão**

    ```
    discord.py>=2.0.0
    ```
*   **Repositório GitHub (**[**Versão Instável**](https://github.com/Rapptz/discord.py)**)**

    ```
    git+https://github.com/Rapptz/discord.py
    ```

{% hint style="info" %}
#### **Melhores Práticas**

* 🔒 Bloqueie dependências críticas com `==` para versões específicas
* 🔄 Use `>=` para pacotes que esperam atualizações
* 💻 Sempre teste com versões exatas antes do deploy
{% endhint %}

***

## **📦 Adicionando Pacotes**

{% stepper %}
{% step %}
**Instale pacotes usando pip.**

```bash
pip install nome-do-pacote
```
{% endstep %}

{% step %}
**Atualize seu arquivo de requisitos.**

```bash
pip freeze --user > requirements.txt
```
{% endstep %}
{% endstepper %}

***

## **⚠️ Notas Importantes**

* Inclua apenas pacotes que você instalou ativamente via pip – módulos importados não equivalem automaticamente a pacotes necessários!
* Para pacotes baseados em GitHub, inclua a URL completa do repositório conforme mostrado nos exemplos.
* Se encontrar problemas de instalação, verifique se todas as versões dos pacotes são compatíveis com sua versão do Python.
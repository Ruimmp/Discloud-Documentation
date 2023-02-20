# 📄 Criar o requirements.txt

É um **simples arquivo de texto** que salva uma lista de **pacotes** necessários pelo seu projeto.&#x20;

## Como criar o arquivo `requirements.txt`?

Comece por entrar no diretório do seu projeto e criar um novo arquivo **txt** e certifique-se de que seja **nomeado para** `requirements.txt`

![](../../../.gitbook/assets/create-requirements.png)

## Adicionar pacotes manualmente (opção 1)

{% hint style="warning" %}
As bibliotecas não são as que você **importa** no seu código, e sim as que você instala pelo **pip install**.
{% endhint %}

#### [discord.py](https://pypi.org/project/discord.py/) (PyPI) (Estável)

Adicione a seguinte linha no seu `requirements.txt`, para que a Discloud instale o **discord.py**

{% code title="requirements.txt" %}
```
discord.py
```
{% endcode %}

Quando não especificamos uma versão, o **pip** sempre tentará instalar a versão mais recente do pacote especificado. Podemos especificar versões das seguintes maneiras:

> * `discord.py==2.0.0` - Define uma versão específica a ser instalada. Fixar a versão dessa forma garante que o seu projeto vai sempre estar funcionando, caso o seu codigo ainda não esteja adaptado para uma versão superior
> * `discord.py>=2.0.0`: Quando usamos o sinal de **`>=`** estamos dizendo que queremos instalar qualquer versão superior ou igual da biblioteca.

#### [discord.py](https://github.com/Rapptz/discord.py) (Github) (Instável)

Adicione a seguinte linha no seu `requirements.txt`, para que a Discloud instale o **discord.py** _(mas a versão instável)_

{% code title="requirements.txt" %}
```python
git+https://github.com/Rapptz/discord.py
```
{% endcode %}

Dessa forma conseguimos instalar pacotes **Python** que estejam disponíveis no **GitHub** mas não no **PyPI**, como versões ainda em **desenvolvimento**.

## Adicionar pacotes automaticamente (opção 2)

Se você tiver o **Python** instalado no seu computador pode executar um simples comando no seu Terminal para colocar todas as **bibliotecas** e as **suas versões** em um `requirements.txt`

{% hint style="warning" %}
Certifique-se de ter todos os pacotes necessários pelo seu projeto instalados no seu computador antes de executar
{% endhint %}

Abra o Terminal no diretório do seu projeto (Windows use: **Shift+Botão Direito** e clique em **Open PowerShell**) e digite:

```sh
pip freeze --user > requirements.txt
```

> **--user** - Apenas a saída de pacotes instaladas pelo usuário

![Todas as dependências foram colocadas automaticamente em requirements.txt](../../../.gitbook/assets/pip.png)

{% hint style="info" %}
Você precisa do **python e pip** instalado no seu computador, caso não esteja instalado siga as instruções abaixo.
{% endhint %}

{% content-ref url="../../../ambiente-local/instalar/python.md" %}
[python.md](../../../ambiente-local/instalar/python.md)
{% endcontent-ref %}

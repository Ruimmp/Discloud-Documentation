---
description: >-
  Instale e gerencie Python localmente (Windows, macOS, Linux) usando instaladores oficiais,
  pacotes do sistema ou pyenv; crie ambientes virtuais.
icon: python
---

# Python

## 🧾 Visão Geral

Python é usado para bots, APIs, automação, scripting e tarefas de dados. A instalação local permite instalar dependências e testar antes de implantar na Discloud.

{% embed url="https://www.python.org" %}

---

## 📥 Instalação

{% tabs %}
{% tab title="🪟 Windows" %}
{% stepper %}
{% step %}
Baixe o instalador mais recente do Python 3 de [https://www.python.org/downloads/](https://www.python.org/downloads/)
{% endstep %}

{% step %}
Marque "Add Python to PATH" e complete a instalação.
{% endstep %}

{% step %}
Reabra o terminal e verifique

```bash
python --version
pip -V
```

{% endstep %}

{% step %}
Crie ambiente virtual opcional

```bash
python -m venv .venv
.venv\\Scripts\\activate
pip install --upgrade pip
```

{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="🐧 Linux" %}
{% tabs %}
{% tab title="Debian/Ubuntu" %}

```bash
sudo apt update
sudo apt install -y python3 python3-pip python3-venv
python3 --version
pip3 -V
python3 -m venv .venv
source .venv/bin/activate
```

{% endtab %}

{% tab title="Fedora" %}

```bash
sudo dnf install -y python3 python3-pip
python3 --version
pip3 -V
python3 -m venv .venv
source .venv/bin/activate
```

{% endtab %}

{% tab title="Arch" %}

```bash
sudo pacman -S --needed python python-pip
python --version
pip -V
python -m venv .venv
source .venv/bin/activate
```

{% endtab %}

{% tab title="pyenv" %}
Dependências (exemplo Debian):

```bash
sudo apt update
sudo apt install -y build-essential libssl-dev zlib1g-dev \
libncurses5-dev libffi-dev libbz2-dev libreadline-dev libsqlite3-dev \
liblzma-dev wget curl
```

Instalar e configurar:

```bash
curl https://pyenv.run | bash
echo 'export PYENV_ROOT="$HOME/.pyenv"' >> ~/.bashrc
echo 'command -v pyenv >/dev/null || export PATH="$PYENV_ROOT/bin:$PATH"' >> ~/.bashrc
echo 'eval "$(pyenv init -)"' >> ~/.bashrc
source ~/.bashrc
pyenv install 3.12.4
pyenv global 3.12.4
python --version
```

{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="🍎 macOS" %}
{% tabs %}
{% tab title="Instalador" %}
Baixe de [python.org](https://www.python.org/downloads/) e execute, então:

```bash
python3 --version
pip3 -V
```

{% endtab %}

{% tab title="Homebrew" %}

```bash
brew update
brew install python
python3 --version
pip3 -V
```

{% endtab %}
{% endtabs %}
{% endtab %}
{% endtabs %}

---

## ✅ Verificação

```bash
python --version
pip -V
```

Se a distribuição usar `python3`, substitua adequadamente.

Se sua distribuição usar `python3`, invoque isso em vez de `python`.

---

## 🗂 Ambientes Virtuais

**O que é**: Um ambiente virtual é uma árvore de diretórios isolada contendo seu próprio interpretador Python e pacotes instalados, separado do seu Python global (sistema).

**Por que usar**:

- Mantém as dependências do projeto isoladas (um projeto pode usar `requests==2.31`, outro `requests==2.29`).
- Evita precisar de instalações de administrador / em todo o sistema.
- Previne conflitos acidentais com pacotes do SO ou outros projetos.
- Faz com que `requirements.txt` reflita apenas o que o projeto realmente precisa (reprodutibilidade ao implantar ou compartilhar).
- Permite testar upgrades com segurança (crie um novo env, instale, compare comportamento).

Criar e ativar:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
```

Instalar dependências e capturar versões:

```bash
pip install -r requirements.txt
pip freeze > requirements.txt
```

---

## 🔄 Atualização

| Tarefa                       | Comando                               |
| ---------------------------- | ------------------------------------- |
| Atualizar pip                | `python -m pip install --upgrade pip` |
| Atualizar um pacote          | `pip install <name> --upgrade`        |
| Instalar novo Python (pyenv) | `pyenv install <version>`             |

---

## 🗃 Comandos Comuns

```bash
pip install requests
pip list
pip freeze > requirements.txt
python main.py
python -m venv .venv
```

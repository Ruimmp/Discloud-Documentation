---
description: >-
  Instale e gerencie Go localmente (Windows, macOS, Linux) usando arquivos
  oficiais ou gerenciadores de pacotes; gerencie módulos com go mod.
icon: golang
---

# Golang

## 🧾 Visão Geral

Go (Golang) é uma linguagem compilada adequada para APIs, workers, CLIs e serviços concorrentes. A instalação local permite construir e testar binários antes de implantar.

{% embed url="https://go.dev" %}

***

## 📥 Instalação (escolha uma)

{% tabs %}
{% tab title="Windows" %}
{% tabs %}
{% tab title="Instalador" %}
{% stepper %}
{% step %}
Baixe o .msi do Windows de [https://go.dev/dl/](https://go.dev/dl/)
{% endstep %}

{% step %}
Execute-o (adiciona Go ao PATH).
{% endstep %}

{% step %}
Reabra o terminal (PowerShell / CMD).
{% endstep %}

{% step %}
Verifique:

```bash
go version
```
{% endstep %}
{% endstepper %}
{% endtab %}

{% tab title="Scoop" %}
```bash
scoop install go
go version
```
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="Linux" %}
{% tabs %}
{% tab title="Tarball" %}
```bash
# Substitua a versão conforme necessário
curl -LO https://go.dev/dl/go1.22.6.linux-amd64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.22.6.linux-amd64.tar.gz
export PATH="/usr/local/go/bin:$PATH"
go version
```

{% hint style="info" %}
Adicione a linha PATH ao \~/.bashrc ou \~/.zshrc para persistir.
{% endhint %}
{% endtab %}

{% tab title="Debian/Ubuntu" %}
```bash
sudo apt update
sudo apt install -y golang-go
go version
```

{% hint style="info" %}
Nota: A versão do repositório pode estar atrasada em relação à mais recente.
{% endhint %}
{% endtab %}

{% tab title="Fedora" %}
```bash
sudo dnf install -y golang
go version
```
{% endtab %}

{% tab title="Arch" %}
```bash
sudo pacman -S --needed go
go version
```
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="macOS" %}
{% tabs %}
{% tab title="Instalador" %}
Baixe o .pkg de [https://go.dev/dl/](https://go.dev/dl/) então:

```bash
go version
```
{% endtab %}

{% tab title="Homebrew" %}
```bash
brew update
brew install go
go version
```
{% endtab %}

{% tab title="Tarball" %}
```bash
curl -LO https://go.dev/dl/go1.22.6.darwin-arm64.tar.gz
sudo rm -rf /usr/local/go
sudo tar -C /usr/local -xzf go1.22.6.darwin-arm64.tar.gz
export PATH="/usr/local/go/bin:$PATH"
go version
```

{% hint style="info" %}
Adicione a exportação PATH ao perfil do shell para persistir.
{% endhint %}
{% endtab %}
{% endtabs %}
{% endtab %}
{% endtabs %}

***

## 🗂 Módulos e Inicialização do Projeto

{% stepper %}
{% step %}
Inicialize um módulo (cria go.mod)

```
mkdir myapp && cd myapp
go mod init example.com/myapp
go get
```
{% endstep %}

{% step %}
Adicione um arquivo `main.go`

```go
package main
import "fmt"
func main() { fmt.Println("hello") }
```
{% endstep %}

{% step %}
Execute

```bash
go run .
```
{% endstep %}

{% step %}
Construa

```bash
go build -o app
```
{% endstep %}
{% endstepper %}

***

## 🔄 Atualização

| Tarefa                          | Comando                 |
| ------------------------------- | ----------------------- |
| Organizar módulos               | `go mod tidy`           |
| Atualizar deps (menor/correção) | `go get -u ./...`       |
| Atualizar módulo único          | `go get -u module/name` |
| Verificar módulos               | `go mod verify`         |

***

## 🗃 Comandos Comuns

```bash
go mod init example.com/project
go mod tidy
go run .
go build -o bin/app
go test ./...
go list -m all
```

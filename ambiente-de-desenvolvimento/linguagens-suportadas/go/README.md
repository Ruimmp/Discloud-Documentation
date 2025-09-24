---
description: Guia completo para hospedar aplicações Go no Discloud.
icon: golang
---

# Go

## 📁 **Preparando os Arquivos**

Antes de fazer upload do seu projeto, você deve **excluir arquivos desnecessários** para otimizar o deploy.

#### ❌ **Arquivos a Excluir**

Certifique-se de que os seguintes arquivos e diretórios **não** sejam incluídos no seu [`.zip`](../../../faq/perguntas-gerais/em-andamento-como-comprimir.md):

```diff
- bin/
- *.exe
- .git/
```

📌 **Use um arquivo** [**`.discloudignore`**](../../../configuracoes/.discloudignore.md) **para excluir automaticamente esses arquivos. Não** exclua `go.mod` ou `go.sum`.

🔗 **Precisa de ajuda para configurar seu** [**`go.mod`**](go.mod.md) **ou encontrar o** [**arquivo principal**](../../../faq/perguntas-gerais/em-andamento-qual-e-o-arquivo-principal.md)**?**

***

### 🌐 **Hospedando Websites & APIs em Go**

Antes de fazer deploy do seu website ou API no Discloud, certifique-se de que você atenda aos seguintes **requisitos**:

✔ [Plano Platinum ou superior](https://discloud.com/plans) é necessário para hospedar websites ou APIs.\
✔ [Um subdomínio deve ser criado](../../../faq/perguntas-gerais/em-andamento-como-criar-um-subdominio.md) antes do deploy.\
✔ <mark style="color:red;">Porta</mark> <mark style="color:red;">`8080`</mark> <mark style="color:red;">é obrigatória</mark> – As aplicações devem escutar nesta porta.

{% tabs %}
{% tab title="🤖 Bot Discord" %}
```go
package main

import (
  "log"
  "os"
  "os/signal"
  "syscall"
  "github.com/bwmarrin/discordgo"
)

func main() {
  token := os.Getenv("DISCORD_TOKEN")
  if token == "" { log.Fatal("DISCORD_TOKEN não definido") }

  dg, err := discordgo.New("Bot " + token)
  if err != nil { log.Fatal(err) }

  dg.AddHandler(func(s *discordgo.Session, r *discordgo.Ready) {
    log.Println("Bot está pronto")
  })

  if err := dg.Open(); err != nil { log.Fatal(err) }
  log.Println("Bot executando. Pressione CTRL+C para sair.")

  stop := make(chan os.Signal, 1)
  signal.Notify(stop, os.Interrupt, syscall.SIGTERM)
  <-stop
  dg.Close()
}
```

> Bots não precisam bindar nenhuma porta HTTP. Eles só precisam manter o processo vivo.
{% endtab %}

{% tab title="⚙️ Servidor HTTP Básico" %}
```go
package main

import (
  "fmt"
  "log"
  "net/http"
)

func main() {
  mux := http.NewServeMux()
  mux.HandleFunc("/", func(w http.ResponseWriter, r *http.Request) {
    fmt.Fprintln(w, "Olá do Go no Discloud!")
  })

  log.Println("Iniciando servidor em :8080")
  if err := http.ListenAndServe(":8080", mux); err != nil {
    log.Fatal(err)
  }
}
```
{% endtab %}

{% tab title="🔀 API REST (chi)" %}
```go
package main

import (
  "net/http"
  "log"
  "github.com/go-chi/chi/v5"
)

func main() {
  r := chi.NewRouter()
  r.Get("/health", func(w http.ResponseWriter, r *http.Request) { w.Write([]byte("ok")) })
  r.Get("/hello/{name}", func(w http.ResponseWriter, r *http.Request) {
    name := chi.URLParam(r, "name")
    w.Write([]byte("Olá, "+name))
  })
  log.Println("API em :8080")
  log.Fatal(http.ListenAndServe(":8080", r))
}
```
{% endtab %}
{% endtabs %}

***

## ✍️ Fazendo Deploy **da Sua Aplicação**

Uma vez que seu projeto esteja **configurado e comprimido**, você pode escolher um dos seguintes **métodos de deploy** no Discloud:

<table data-card-size="large" data-view="cards"><thead><tr><th data-card-target data-type="content-ref"></th><th align="center"></th><th data-hidden></th><th data-hidden></th><th data-hidden></th></tr></thead><tbody><tr><td><a href="../../../como-hospedar-usando/painel-de-controle.md">painel-de-controle.md</a></td><td align="center">Faça upload e gerencie sua aplicação via interface web.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/bot-do-discord.md">bot-do-discord.md</a></td><td align="center">Faça deploy diretamente através dos comandos do bot Discord do Discloud.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/visual-studio-code.md">visual-studio-code.md</a></td><td align="center">Integre com VS Code para gerenciamento contínuo de projetos.</td><td></td><td></td><td></td></tr><tr><td><a href="../../../como-hospedar-usando/cli.md">cli.md</a></td><td align="center">Use a interface de linha de comando para deploy rápido e eficiente.</td><td></td><td></td><td></td></tr></tbody></table>

---
description: >-
  Aprenda a hospedar o seu BOT Python com 1 servidor Lavalink na mesma
  instancia na DisCloud
---

# Python

## Introdução

Para usar este código basta fazer: 

1. Baixar a código pelas [`Releases`](https://github.com/discloud/lavalink-python/releases) ou [Clique Aqui](https://github.com/discloud/lavalink-python/releases/latest/download/lavalink-python.zip) 

2. Depois de baixado, basta colocar o código do seu Bot no diretório `bot` 

3. No arquivo `config.json` no `fileRunBot` altere o nome do arquivo principal \(no caso está `main.py` mas se for outro nome \(como por exemplo `bot.py`\) troque para o nome correto\) 4. No seu codigo, área onde você conecta o Lavalink por favor coloque este dados:

> ```python
> {
>   host: "localhost",
>   port: 2333,
>   password: "discloud"
> }
> ```
>
> Depois de tudo feito e envie para a DisCloud colocando `lavalink.py` como Arquivo Principal

### FAQ

### O Java/Lavalink está corrompido o que eu faço agora?

A maneira mais rápida de resolver é deletando o diretório `Java` \(que é o diretório onde se localiza os arquivos do OpenJDK e do LavaLink\) e iniciando o BOT de novo que irá baixar tudo de novo

### Quero fazer backup do meu arquivos porém é muito pesado o que eu faço?

Para reduzir o peso do download do backup você pode remover:

* O diretório `java`
* Caso não queira receber os no backup dos logs remova também o diretório `logs`

### Porque o meu BOT demora muito para ficar online?

No primeiro Deploy é claro que demora mais algum tempo que esperado já antes de iniciar o Bot tem que fazer o download do **OpenJDK** e do Lavalink \(e claro isso depende da internet\) e iniciar o Lavalink primeiro.  
 No próximos Deploy é só esperar o Lavalink iniciar

**Obs:** ao remover o diretório `Java` vai ser como o se fosse o primeiro Deploy ao inciar!!

### Parece que este código não foi atualizado, como posso atualizá-lo?

A maneira mais rápida na DisCloud é só deletar a diretório `Java` \(pode ter atualização nos arquivos\) baixar a nova [`Release`](https://github.com/discloud/lavalink-python/releases/latest/download/lavalink-python.zip), fazer alteração do `fileRunBot` que já fui comentada e enviar as alterações.

### Como faço alterações do meu Bot com este código?

De maneira simples o seu arquivo zip de alteração de código tem de estar assim:

```text
zip > bot > <seu codigo>
```

Lembre-se de sempre colocar o código do seu projeto na pasta Bot, caso não faça isso o commit salvará seus arquivos na raiz da instancia e seu Bot não funcionará 


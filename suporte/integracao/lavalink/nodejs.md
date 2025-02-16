---
description: >-
  Aprenda a hospedar o seu BOT JavaScript com 1 servidor Lavalink na mesma
  instancia na DisCloud
---

# NodeJS

## Introdução

Para usar este código basta fazer: 

1. Baixar a código pelas [`Releases`](https://github.com/discloud/lavalink-nodejs/releases) ou [Clique Aqui](https://github.com/discloud/lavalink-nodejs/releases/latest/download/lavalink-nodejs.zip) 

2. Depois de baixado, basta colocar o código do seu Bot no diretório `bot` 

3. No arquivo `config.json` no `fileRunBot` altere o nome do arquivo principal \(no caso está `bot.js` mas se for outro nome \(como por exemplo `index.js`\) troque para o nome correto\) 4. No seu código, área onde você conecta o Lavalink por favor coloque estes dados:

> ```javascript
> {
>   host: "localhost",
>   port: 2333,
>   password: "discloud"
> }
> ```
>
> Depois de tudo feito e envie para a DisCloud colocando `index.js` como Arquivo Principal

### FAQ

### O Java/Lavalink está corrompido o que eu faço agora?

A maneira mais rápida de resolver é deletando o diretório `Java` \(que é o diretório onde se localiza os arquivos do OpenJDK e do LavaLink\) e iniciando o BOT de novo que irá baixar tudo novamente

### Quero fazer backup do meu arquivos, porém é muito pesado o que eu faço?

Para reduzir o peso do download do backup você pode remover:

* O diretório `java`
* O diretório `node_modules` que se encontra no diretório `Bot` \(já que a DisCloud não consegue controlar esse `node_modules` devido não estar na raiz da Instância\)
* Caso não queira receber os logs no backup remova também o diretório `logs` (caso os `logMODE` no `config.json` esteja `true`)

### Porque o meu BOT demora muito para ficar online?

No primeiro Deploy é claro que demora mais algum tempo que esperado já antes de iniciar o Bot tem que fazer o download do **OpenJDK** e do Lavalink \(e claro isso depende da internet\) e iniciar o Lavalink primeiro.  
 No próximo Deploy é só esperar o Lavalink iniciar

**Obs.:** ao remover o diretório `Java` vai ser como o se fosse o primeiro Deploy ao iniciar!!

### Parece que este código não foi atualizado, como posso atualizá-lo?

A maneira mais rápida na DisCloud é só deletar o diretório `Java` \(pode ter atualização nos arquivos\) baixar a nova [`Release`](https://github.com/discloud/lavalink-nodejs/releases/latest/download/lavalink-nodejs.zip), fazer alteração do `fileRunBot` que já foi comentada e enviar as alterações.

### Como faço alterações do meu Bot com este código?

De maneira simples o seu arquivo zip de alteração de código tem de estar assim:

```text
zip > bot > <seu código>
```

Lembre-se de sempre colocar o código do seu projeto na pasta Bot, caso não faça isso o commit salvará seus arquivos na raiz da instância e seu Bot não funcionará 


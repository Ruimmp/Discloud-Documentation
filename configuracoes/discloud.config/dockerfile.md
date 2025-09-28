---
description: >-
  Use um Dockerfile para fazer o upload de aplicações na Discloud, dando a você
  mais liberdade para usar suas tecnologias favoritas.
icon: docker
---

# Dockerfile

## ❓ **O que é um Dockerfile?**

Um **Dockerfile** é um arquivo de texto simples que contém uma série de comandos usados para definir como criar uma [**imagem Docker**](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/). Ele descreve as etapas que o Docker deve seguir para configurar um **ambiente containerizado**, incluindo:\
✔ O **sistema operacional**\
✔ **Dependências** necessárias\
✔ **Arquivos** do projeto\
✔ **Comandos e configurações** da aplicação

📌 **Saiba mais:** [Referência Completa do Dockerfile](https://docs.docker.com/engine/reference/builder/)

***

## ⚙️ **Como Usar um Dockerfile na Discloud**

{% stepper %}
{% step %}
Crie seu Dockerfile.

Adicione as instruções necessárias, dependências, variáveis de ambiente e configurações.
{% endstep %}

{% step %}
Defina o MAIN no [`discloud.config`](./)

<pre class="language-properties" data-title="discloud.config"><code class="lang-properties"><a data-footnote-ref href="#user-content-fn-1"># ...</a>
MAIN=Dockerfile
# ...
</code></pre>
{% endstep %}

{% step %}
Certifique-se de que ambos os arquivos estejam na [raiz do seu projeto](../../faq/perguntas-gerais/o-que-e-a-raiz-do-projeto.md).

Seu **Dockerfile** e [`discloud.config`](./) devem estar no [**diretório raiz**](../../faq/perguntas-gerais/o-que-e-a-raiz-do-projeto.md) do seu projeto.
{% endstep %}

{% step %}
hospede como de costume.

Faça upload do seu projeto como faria com uma [upload normal da Discloud](https://github.com/discloud/docs/blob/portuguese-revamp/configuracoes/discloud.config/broken-reference/README.md).
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
**🚨 Importante:**

* **Conhecimento básico de Docker** é necessário para usar este recurso.
* **Configurações incorretas** no Dockerfile podem impedir que seu app funcione corretamente.
* **Junte-se ao nosso servidor Discord para obter ajuda**: [https://discord.discloudbot.com](https://discord.discloudbot.com/)
{% endhint %}

***

## 🔒 **Redes Privadas Docker (Suporte VLAN)**

O Discloud suporta **redes privadas** entre aplicações Docker, permitindo **comunicação local** entre serviços. Isso é útil para:\
✔ **APIs** (Express, Fastify, Lavalink)\
✔ **Bancos de dados** (MySQL, PostgreSQL, MongoDB)\
✔ **Serviços de cache** (Redis, Memcached, KeyDB)

### 🔧 **Habilitando Redes Privadas no** [**`discloud.config`**](./)

Para ativar **redes privadas**, adicione as seguintes opções no seu arquivo de configuração:

```ini
# ...
NAME=Meu Servidor Mongo
MAIN=Dockerfile
VLAN=true
HOSTNAME=mymongoserver
#       |      ^     |
#       |      Nome da rede privada para esta aplicação
# ...
```

{% hint style="info" %}
📌 **Certifique-se de expor as portas corretas no seu Dockerfile!**
{% endhint %}

### 🌍 **Conectando-se a Redes Privadas**

Com **VLAN habilitada**, outras aplicações Docker podem acessar seu serviço hospedado:

```javascript
import mongoose from "mongoose";

const uri = "mongodb://mymongoserver:27017/mydatabase";
//                    |      ^      |
//       Nome da rede privada do seu servidor MongoDB

try {
  await mongoose.connect(uri);
  console.log("Conectado com sucesso ao MongoDB!");
} catch (error) {
  console.error("Erro ao conectar ao MongoDB:", error);
}
```

***

## 🪅 **Exemplos de Aplicações Usando Dockerfile**

Abaixo estão **exemplos de diferentes aplicações** que podem ser hospedadas usando **Dockerfile** na Discloud.

{% tabs %}
{% tab title="🤖 Bots Discord" %}
{% tabs %}
{% tab title="🟨 Bot JavaScript" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem atual do Node.js LTS (20.18)
FROM node:20.18-alpine

# Crie um diretório de trabalho para a aplicação
WORKDIR /app

# Copie os arquivos necessários para o container
COPY package*.json ./

# Instale as dependências
RUN npm install

# Copie o resto do código para o container
COPY . .

# Comando para iniciar a aplicação
CMD ["node", "index.js"]
```
{% endcode %}
{% endtab %}

{% tab title="🔵 Bot TypeScript" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem atual do Node.js LTS (20.18)
FROM node:20.18-alpine

# Crie um diretório de trabalho para a aplicação
WORKDIR /app

# Copie os arquivos necessários para o container
COPY package*.json tsconfig.json ./

# Instale as dependências
RUN npm install

# Compile TypeScript para JavaScript
RUN npm run build

# Copie o resto do código para o container
COPY . .

# Comando para iniciar o bot compilado
CMD ["node", "dist/index.js"]
```
{% endcode %}
{% endtab %}

{% tab title="🐍 Bot Python" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do Python 3.11 como base
FROM python:3.11-slim

# Crie o diretório de trabalho para o bot
WORKDIR /app

# Copie os arquivos necessários para o container
COPY requirements.txt ./

# Instale as dependências do projeto
RUN pip install --no-cache-dir -r requirements.txt

# Copie o resto do código do bot para o container
COPY . .

# Comando para iniciar o bot
CMD ["python", "bot.py"]
```
{% endcode %}
{% endtab %}

{% tab title="☕ Bot Java" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do Maven para construir o projeto
FROM maven:3.9.6-eclipse-temurin-17 as build

# Defina o diretório de trabalho
WORKDIR /app

# Copie o arquivo pom.xml e outros arquivos necessários para resolver dependências
COPY pom.xml ./

# Baixe as dependências para otimizar o cache
RUN mvn dependency:go-offline -B

# Copie o código fonte para o container
COPY src ./src

# Compile o projeto e crie o arquivo JAR
RUN mvn package -DskipTests

# Use a imagem oficial do JRE para execução
FROM eclipse-temurin:17-jre-alpine

# Defina o diretório de trabalho no container final
WORKDIR /app

# Copie o arquivo JAR do estágio de build
COPY --from=build /app/target/*.jar bot.jar

# Comando para iniciar o bot
CMD ["java", "-jar", "bot.jar"]
```
{% endcode %}
{% endtab %}

{% tab title="🐹 Go" %}
{% code title="Dockerfile" %}
```docker
# Bot Go mínimo com apenas biblioteca padrão (go.sum vazio)
FROM docker.io/library/golang:1.14
WORKDIR /app

# Copie arquivos de módulo (mesmo se go.sum estiver vazio, deve existir)
COPY go.mod go.sum ./
RUN go mod download

# Copie fonte
COPY . .
RUN go build -o bot .

# (Nenhuma porta necessária para bots Discord)
CMD ["./bot"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="🌐 Aplicações Web & APIs" %}
{% tabs %}
{% tab title="🟩 Site HTML" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do NGINX
FROM nginx:latest

# Remova a configuração padrão do NGINX e copie uma personalizada
COPY nginx.conf /etc/nginx/nginx.conf

# Copie o conteúdo do site estático para o diretório de serviço do NGINX
COPY ./site /usr/share/nginx/html

# Exponha a porta 80 para acesso web
EXPOSE 80

# Inicie o servidor NGINX
CMD ["nginx", "-g", "daemon off;"]
```
{% endcode %}
{% endtab %}

{% tab title="📡 API Web Express" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do Node.js (LTS)
FROM node:20.18-alpine

# Defina o diretório de trabalho
WORKDIR /app

# Copie os arquivos package.json
COPY package*.json ./

# Instale as dependências
RUN npm install

# Copie o resto dos arquivos da aplicação
COPY . .

# Exponha a porta 8080 para acesso ao site
EXPOSE 8080

# Comando para iniciar o servidor Node.js
CMD ["npm", "start"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="💾 Bancos de Dados" %}
{% tabs %}
{% tab title="🍃 MongoDB" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do MongoDB
FROM mongo:latest

# Defina variáveis de ambiente para configuração inicial
ENV MONGO_INITDB_ROOT_USERNAME=root
ENV MONGO_INITDB_ROOT_PASSWORD=rootpassword
ENV MONGO_INITDB_DATABASE=mydatabase

# Exponha a porta padrão do MongoDB
EXPOSE 27017

# Comando padrão para iniciar o MongoDB
CMD ["mongod"]
```
{% endcode %}
{% endtab %}

{% tab title="🐘 PostgreSQL" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do PostgreSQL
FROM postgres:latest

# Defina variáveis de ambiente para configuração inicial
ENV POSTGRES_PASSWORD=rootpassword
ENV POSTGRES_DB=mydatabase
ENV POSTGRES_USER=myuser

# Exponha a porta padrão do PostgreSQL
EXPOSE 5432

# Comando para iniciar o PostgreSQL
CMD ["postgres"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}
{% endtabs %}

[^1]: **Nota:** Os **`...`** indicam apenas a continuação de outras opções anteriores ou subsequentes que não são relevantes para mencionar nesta página.

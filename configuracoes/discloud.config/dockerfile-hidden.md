---
description: >-
  Use um Dockerfile para fazer o upload de aplicações na Discloud, dando a você
  mais liberdade para usar suas tecnologias favoritas.
icon: docker
hidden: true
---

# Dockerfile Hidden

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
#### **🚨 Importante:**

* **Conhecimento básico de Docker** é necessário para usar este recurso.
* **Configurações incorretas** no Dockerfile podem impedir que seu app funcione corretamente.
* **Junte-se ao nosso servidor Discord para obter ajuda**: [https://discord.discloudbot.com](https://discord.discloudbot.com/)
{% endhint %}

***

## 🔐 **Requisitos de Compatibilidade com a Discloud**

Para que sua aplicação seja compatível com a infraestrutura da Discloud ao usar Dockerfile, siga as seguintes instruções:

{% hint style="warning" %}
- O processo final do container **deve executar como usuário de UID `1000`** (usuário padrão da Discloud).
- Qualquer arquivo/diretório que precise ser **persistido ou escrito em tempo de execução** deve ficar dentro de **`/home/discloud`**.
{% endhint %}

***

## 🪅 **Exemplos de Aplicações Usando Dockerfile**

Abaixo estão **exemplos de diferentes aplicações** que podem ser hospedadas usando **Dockerfile** na Discloud.

{% tabs %}
{% tab title="🤖 Bots Discord" %}
{% tabs %}
{% tab title="🟨 Bot JavaScript" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem atual do Node.js
FROM node:20.18-alpine

# Crie um diretório de trabalho para a aplicação
WORKDIR /home/discloud/app

# Copie os arquivos necessários para o container
COPY package*.json ./

# Instale as dependências
RUN npm install --production

# Copie o resto do código para o container
COPY . .

# Garanta as permissões corretas
RUN chown -R 1000:1000 /home/discloud

# Troque para o usuário
USER 1000

# Comando para iniciar a aplicação
CMD ["node", "index.js"]
```
{% endcode %}
{% endtab %}

{% tab title="🔵 Bot TypeScript" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem atual do Node.js
FROM node:20.18-alpine

# Crie um diretório de trabalho para a aplicação
WORKDIR /home/discloud/app

# Copie os arquivos necessários para o container
COPY package*.json tsconfig.json ./

# Instale as dependências
RUN npm install --production

# Copie o resto do código para o container
COPY . .

# Compile TypeScript para JavaScript e ajuste permissões
RUN npm run build \
 && chown -R 1000:1000 /home/discloud

# Troque para o usuário
USER 1000

# Comando para iniciar o bot compilado
CMD ["node", "dist/index.js"]
```
{% endcode %}
{% endtab %}

{% tab title="🐍 Bot Python" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do Python
FROM python:3.11-slim

# Crie o diretório de trabalho para o bot
WORKDIR /home/discloud/app

# Copie os arquivos necessários para o container
COPY requirements.txt ./

# Instale as dependências do projeto
RUN pip install --no-cache-dir -r requirements.txt \
 && mkdir -p /home/discloud/{data,logs} \
 && chown -R 1000:1000 /home/discloud

# Copie o resto do código do bot para o container
COPY . .

# Garanta as permissões corretas
RUN chown -R 1000:1000 /home/discloud

# Troque para o usuário
USER 1000

# Comando para iniciar o bot
CMD ["python", "bot.py"]
```
{% endcode %}
{% endtab %}

{% tab title="☕ Bot Java" %}
{% code title="Dockerfile" %}
```docker
# Use a imagem oficial do Maven para construir o projeto
FROM maven:3.9.6-eclipse-temurin-17 AS build

# Defina o diretório de trabalho
WORKDIR /workspace

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

# Defina o diretório de trabalho no container final e ajuste permissões
RUN addgroup -g 1000 discloud 2>/dev/null || true \
 && adduser -D -u 1000 -G discloud discloud 2>/dev/null || true \
 && mkdir -p /home/discloud/app \
 && chown -R 1000:1000 /home/discloud

# Defina o diretório de trabalho
WORKDIR /home/discloud/app

# Copie o JAR construído do estágio anterior
COPY --from=build /workspace/target/*.jar bot.jar

# Troque para o usuário
USER 1000

# Comando para iniciar o bot
CMD ["java", "-jar", "bot.jar"]
```
{% endcode %}
{% endtab %}

{% tab title="🐹 Go" %}
{% code title="Dockerfile" %}
```docker
# Bot Go mínimo com apenas biblioteca padrão (go.sum vazio)
FROM golang:1.22-alpine AS build

# Define o diretório de trabalho
WORKDIR /build

# Copie arquivos de módulo (mesmo se go.sum estiver vazio, deve existir)
COPY go.mod go.sum ./

# Baixe as dependências
RUN go mod download

# Copie o resto do código do bot para o container
COPY . .

# Compile o binário do bot
RUN go build -o bot .

# Use uma imagem mínima para rodar o binário
FROM alpine:3.20

# Ajuste permissões e prepare o ambiente de execução
RUN addgroup -g 1000 discloud 2>/dev/null || true \
 && adduser -D -u 1000 -G discloud discloud 2>/dev/null || true \
 && mkdir -p /home/discloud/app \
 && chown -R 1000:1000 /home/discloud

# Defina o diretório de trabalho
WORKDIR /home/discloud/app

# Copie o binário compilado do estágio anterior
COPY --from=build /build/bot ./bot

# Troque para o usuário
USER 1000

# Comando para iniciar o bot
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
WORKDIR /home/discloud/app

# Copie os arquivos package.json
COPY package*.json ./

# Instale as dependências
RUN npm install --production

# Copie o resto dos arquivos da aplicação
COPY . .

# Garanta as permissões corretas
RUN chown -R 1000:1000 /home/discloud

# Troque para o usuário
USER 1000

# Exponha a porta 8080 para acesso ao site
EXPOSE 8080

# Comando para iniciar o servidor Node.js
CMD ["npm", "start"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

[^1]: **Nota:** Os **`...`** indicam apenas a continuação de outras opções anteriores ou subsequentes que não são relevantes para mencionar nesta página.

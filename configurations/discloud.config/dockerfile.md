---
description: >-
  Use a Dockerfile to deploy applications to Discloud, giving you more freedom
  to use your favorite technologies.
icon: docker
---

# Dockerfile

## ❓ **What is a Dockerfile?**

A **Dockerfile** is a simple text file that contains a series of commands used to define how to create a [**Docker image**](https://docs.docker.com/get-started/docker-concepts/the-basics/what-is-an-image/). It describes the steps that Docker must follow to set up a **containerized environment**, including:\
✔ The **operating system**\
✔ Required **dependencies**\
✔ Project **files**\
✔ Application **commands and configurations**

📌 **Learn more:** [Complete Dockerfile Reference](https://docs.docker.com/engine/reference/builder/)

***

## ⚙️ **How to Use a Dockerfile in Discloud**

{% stepper %}
{% step %}
Create your Dockerfile.

Add the necessary instructions, dependencies, environment variables, and configurations.
{% endstep %}

{% step %}
Set the MAIN in [`discloud.config`](./)

<pre class="language-properties" data-title="discloud.config"><code class="lang-properties"><a data-footnote-ref href="#user-content-fn-1"># ...</a>
MAIN=Dockerfile
# ...
</code></pre>
{% endstep %}

{% step %}
Ensure both files are in the [root of your project](../../faq/general-questions/what-is-the-root-of-the-project.md).

Your **Dockerfile** and [`discloud.config`](./) must be in the [**root directory**](../../faq/general-questions/what-is-the-root-of-the-project.md) of your project.
{% endstep %}

{% step %}
Deploy as usual.

Upload your project as you would with a normal [Discloud deployment](broken-reference).
{% endstep %}
{% endstepper %}

{% hint style="warning" %}
#### 🚨 **Important:**

* **Basic knowledge of Docker** is required to use this feature.
* **Incorrect configurations** in the Dockerfile can prevent your app from running correctly.
* **Join our Discord server for help**: [https://discord.discloudbot.com](https://discord.discloudbot.com/)
{% endhint %}

***

## 🔒 **Private Docker Networks (VLAN Support)**

Discloud supports **private networks** between Docker applications, allowing **local communication** between services. This is useful for:\
✔ **APIs** (Express, Fastify, Lavalink)\
✔ **Databases** (MySQL, PostgreSQL, MongoDB)\
✔ **Cache services** (Redis, Memcached, KeyDB)

### 🔧 **Enabling Private Networks in** [**`discloud.config`**](./)

To activate **private networking**, add the following options in your configuration file:

```ini
# ...
NAME=My Mongo Server
MAIN=Dockerfile
VLAN=true
HOSTNAME=mymongoserver
#       |      ^     |
#       |      Private network name for this application
# ...
```

{% hint style="info" %}
📌 **Make sure to expose the correct ports in your Dockerfile!**
{% endhint %}

### 🌍 **Connecting to Private Networks**

With **VLAN enabled**, other Docker applications can access your deployed service:

```javascript
import mongoose from "mongoose";

const uri = "mongodb://mymongoserver:27017/mydatabase";
//                    |      ^      |
//       Private network name of your MongoDB server application

try {
    await mongoose.connect(uri);
    console.log("Successfully connected to MongoDB!");
} catch (error) {
    console.error("Error connecting to MongoDB:", error);
}
```

***

## 🪅 **Examples of Applications Using Dockerfile**

Below are **examples of different applications** that can be deployed using **Dockerfile** on Discloud.

{% tabs %}
{% tab title="🤖 Discord Bots" %}
{% tabs %}
{% tab title="🟨 JavaScript Bot" %}
{% code title="Dockerfile" %}
```docker
# Use the current Node.js LTS image (20.18)
FROM node:20.18-alpine

# Create a working directory for the application
WORKDIR /app

# Copy the necessary files to the container
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the code to the container
COPY . .

# Command to start the application
CMD ["node", "index.js"]
```
{% endcode %}
{% endtab %}

{% tab title="🔵 TypeScript Bot" %}
{% code title="Dockerfile" %}
```docker
# Use the current Node.js LTS image (20.18)
FROM node:20.18-alpine

# Create a working directory for the application
WORKDIR /app

# Copy the necessary files to the container
COPY package*.json tsconfig.json ./

# Install dependencies
RUN npm install

# Compile TypeScript to JavaScript
RUN npm run build

# Copy the rest of the code to the container
COPY . .

# Command to start the compiled bot
CMD ["node", "dist/index.js"]
```
{% endcode %}
{% endtab %}

{% tab title="🐍 Python Bot" %}
{% code title="Dockerfile" %}
```docker
# Use the official Python 3.11 image as the base
FROM python:3.11-slim

# Create the working directory for the bot
WORKDIR /app

# Copy the necessary files to the container
COPY requirements.txt ./

# Install project dependencies
RUN pip install --no-cache-dir -r requirements.txt

# Copy the rest of the bot's code to the container
COPY . .

# Command to start the bot
CMD ["python", "bot.py"]
```
{% endcode %}
{% endtab %}

{% tab title="☕ Java Bot" %}
{% code title="Dockerfile" %}
```docker
# Use the official Maven image to build the project
FROM maven:3.9.6-eclipse-temurin-17 as build

# Set the working directory
WORKDIR /app

# Copy the pom.xml file and other necessary files to resolve dependencies
COPY pom.xml ./

# Download dependencies to optimize cache
RUN mvn dependency:go-offline -B

# Copy the source code to the container
COPY src ./src

# Compile the project and create the JAR file
RUN mvn package -DskipTests

# Use the official JRE image for execution
FROM eclipse-temurin:17-jre-alpine

# Set the working directory in the final container
WORKDIR /app

# Copy the JAR file from the build stage
COPY --from=build /app/target/*.jar bot.jar

# Command to start the bot
CMD ["java", "-jar", "bot.jar"]
```
{% endcode %}
{% endtab %}

{% tab title="🐹 Go" %}
{% code title="Dockerfile" %}
```docker
# Minimal Go bot with only standard library (empty go.sum)
FROM docker.io/library/golang:1.14
WORKDIR /app

# Copy module files (even if go.sum is empty it should exist)
COPY go.mod go.sum ./
RUN go mod download

# Copy source
COPY . .
RUN go build -o bot .

# (No port needed for Discord bots)
CMD ["./bot"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="🌐 Web Applications & APIs" %}
{% tabs %}
{% tab title="🟩 HTML Website" %}
{% code title="Dockerfile" %}
```docker
# Use the official NGINX image
FROM nginx:latest

# Remove the default NGINX config and copy a custom one
COPY nginx.conf /etc/nginx/nginx.conf

# Copy the static site content to NGINX's serving directory
COPY ./site /usr/share/nginx/html

# Expose port 80 for web access
EXPOSE 80

# Start NGINX server
CMD ["nginx", "-g", "daemon off;"]
```
{% endcode %}
{% endtab %}

{% tab title="📡 Express Web API" %}
{% code title="Dockerfile" %}
```docker
# Use the official Node.js image (LTS)
FROM node:20.18-alpine

# Set the working directory
WORKDIR /app

# Copy the package.json files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Expose port 8080 for website access
EXPOSE 8080

# Command to start the Node.js server
CMD ["npm", "start"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}

{% tab title="💾 Databases" %}
{% tabs %}
{% tab title="🍃 MongoDB" %}
{% code title="Dockerfile" %}
```docker
# Use the official MongoDB image
FROM mongo:latest

# Set environment variables for initial configuration
ENV MONGO_INITDB_ROOT_USERNAME=root
ENV MONGO_INITDB_ROOT_PASSWORD=rootpassword
ENV MONGO_INITDB_DATABASE=mydatabase

# Expose the default MongoDB port
EXPOSE 27017

# Default command to start MongoDB
CMD ["mongod"]
```
{% endcode %}
{% endtab %}

{% tab title="🐘 PostgreSQL" %}
{% code title="Dockerfile" %}
```docker
# Use the official PostgreSQL image
FROM postgres:latest

# Set environment variables for initial configuration
ENV POSTGRES_PASSWORD=rootpassword
ENV POSTGRES_DB=mydatabase
ENV POSTGRES_USER=myuser

# Expose the default PostgreSQL port
EXPOSE 5432

# Command to start PostgreSQL
CMD ["postgres"]
```
{% endcode %}
{% endtab %}
{% endtabs %}
{% endtab %}
{% endtabs %}

[^1]: **Note:** The **`...`** only indicate the continuation of other previous or subsequent options that are not relevant to mention on this page.

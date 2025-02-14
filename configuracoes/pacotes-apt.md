---
description: >-
  Guia detalhado sobre como adicionar e configurar pacotes APT no container da
  sua aplicação na Discloud.
---

# 📦 Pacotes (APT)

O **APT (Advanced Package Tool)** é o sistema padrão de gerenciamento de pacotes em distribuições Linux baseadas no Debian. Na **Discloud**, você pode facilmente configurar pacotes APT que sua aplicação precisa diretamente no container.

***

## ⚙️ Como Adicionar Pacotes

Para adicionar pacotes ao container da sua aplicação, basta listá-los no campo `APT=` dentro do arquivo `discloud.config`.

{% hint style="info" %}
Caso precise instalar mais de um pacote, basta separá-los usando vírgulas e espaços.
{% endhint %}

***

### ✏️ Exemplo de configuração:

{% code title="discloud.config" %}
```ini
...
APT=tools
...
```
{% endcode %}

{% hint style="info" %}
**Observação** \
\
Os três pontos (`...`) indicam continuidade de outras configurações no `discloud.config`. A linha `APT` deve ser ajustada conforme as opções abaixo para a linguagem desejada.
{% endhint %}

***

## 🛠️ Pacotes Disponíveis

Abaixo estão alguns dos pacotes APT mais comuns que podem ser úteis para seu projeto.

<table><thead><tr><th width="173">Nome do pacote</th><th>Descrição</th><th>Dependências</th></tr></thead><tbody><tr><td>Canvas</td><td>Biblioteca gráfica para renderização e manipulação de imagens.</td><td>libcairo2, libpango1.0-dev, libjpeg-dev, libgif-dev, librsvg2-dev, libgbm-dev</td></tr><tr><td>Puppeteer</td><td>Uma biblioteca Node.js que fornece uma API de alto nível para controlar o Chrome ou Chromium por meio do protocolo DevTools.</td><td>libglib2.0-0, libnss3, libatk1.0-0, libatk-bridge2.0-0, libcups2, libdrm2, libxcomposite1, libxdamage1, libxfixes3, libxrandr2, libgbm1, libxkbcommon0, libpango-1.0-0, libcairo2, libasound2, libgtk-3-0, libxshmfence-dev, libdrm-dev, libgbm-dev, libx11-xcb-dev</td></tr><tr><td>Java</td><td>Instala o OpenJDK Java runtime.</td><td>default-jre</td></tr><tr><td>FFmpeg</td><td>Uma solução completa para gravar, converter e transmitir áudio e vídeo.</td><td>ffmpeg</td></tr><tr><td>LibGL</td><td>Implementa a interface GLX, bem como os principais pontos de entrada da API OpenGL.</td><td>libsm6, libxext6</td></tr><tr><td>Tools</td><td>Ferramentas úteis e essenciais para a maioria dos apps.</td><td>curl, git, wget, make, cmake</td></tr><tr><td>OpenSSL</td><td>Uma biblioteca criptográfica que implementa os protocolos SSL e TLS.</td><td>pkg-config, libssl-dev</td></tr></tbody></table>

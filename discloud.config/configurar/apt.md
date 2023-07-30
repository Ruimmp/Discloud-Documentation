# 📦 APT (Instale Pacotes)

O **APT (Advanced package tool**), faz referência ao instalador de pacotes utilizado em distribuições Linux baseadas em Debian ou Ubuntu.\
\
Na **DisCloud**, você pode adicionar alguns destes pacotes no container da sua aplicação em caso de necessidade.

## :gear: Como Utilizar

Consulte o pacote[^1] necessário para o seu projeto e coloque em `APT=`

{% hint style="info" %}
Se você necessitar de utilizar mais de **1 pacote**, separe por `vírgulas e espaços`, como no exemplo abaixo
{% endhint %}

<pre class="language-typescript" data-title="discloud.config"><code class="lang-typescript">...
<strong>APT=tools, ffmpeg
</strong>...
</code></pre>

> Observação: Os `...` apenas indicam continuidade de outras opções anteriores ou posteriores à linha APT, que não são revelantes e mencionados nesta página.

### Pacotes disponíveis

<table><thead><tr><th width="177.47811180687387">Nome Do Pacote</th><th width="354">Descrição</th><th width="395" data-type="select" data-multiple>Dependências Linux</th></tr></thead><tbody><tr><td>canvas</td><td>Dependencias necessárias para o correto funcionamento do Canvas</td><td></td></tr><tr><td>puppeteer</td><td>Dependencias necessárias para o correto funcionamento do Puppeteer</td><td></td></tr><tr><td>java</td><td>Instala o OpenJDK Java runtime</td><td></td></tr><tr><td>ffmpeg</td><td>🎵 Uma solução completa para gravar, converter e transmitir áudio e vídeo <mark style="color:green;">(necessário para bots de música)</mark></td><td></td></tr><tr><td>libgl</td><td>A libGL implementa a interface GLX, bem como os principais pontos de entrada da API OpenGL.</td><td></td></tr><tr><td>tools</td><td>Ferramentas úteis e essenciais para a maioria dos apps</td><td></td></tr><tr><td>openssl</td><td>Uma biblioteca criptográfica que implementa os protocolos SSL e TLS</td><td></td></tr></tbody></table>

[^1]: Coloque apenas os pacotes abaixo de "Nome Do Pacote" no seu "APT=".&#x20;

    As dependências são apenas o que será instalado pela DisCloud

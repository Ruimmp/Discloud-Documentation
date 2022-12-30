# Bot muito pesado

## :wastebasket: Dicas para diminuir o tamanho do projeto

Verifique se as seguintes **pastas** e **arquivos** se encontram no seu projeto e remova-os:

* **pasta** `node_modules` (apenas disponível em projetos [JavaScript](../linguagens/javascript/#arquivos), não é necessária e a **DisCloud** irá baixar todos os módulos necessários por conta própria)
* **pasta** `.git` (Não é necessário na **DisCloud**, esta pasta contém todas as informações necessárias para o controle de versão do [Git](../integracao/github-e-gitlab/), pode ser necessário manter localmente se você trabalhar com [Git](../integracao/github-e-gitlab/).
* **arquivos** `ffmpeg` (você pode instalar o ffmpeg na DisCloud consulte [aqui](../../discloud.config/configurar/create.md))

## :file\_folder: O projeto continua pesado

### Métodos alternativos

#### [DisCloud API](../../api/usar-a-api.md)

Se o arquivo `.zip` do seu projeto tiver um tamanho `<=100mb` pode fazer o Upload pela nossa API

<figure><img src="../../.gitbook/assets/discloud-api-up.png" alt=""><figcaption><p>Examplo com Insomnia</p></figcaption></figure>

#### [Transfer.sh](https://transfer.sh/)

Se o arquivo `.zip` do seu projeto tiver um tamanho `>=100mb` pode fazer o Upload pelo [Transfer.sh](https://transfer.sh/)

<figure><img src="../../.gitbook/assets/transfer.sh-example.png" alt=""><figcaption></figcaption></figure>

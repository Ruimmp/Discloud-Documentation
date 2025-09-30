---
description: >-
  Habilite redes privadas entre aplicações Discloud usando VLAN e HOSTNAME no
  discloud.config.
icon: network-wired
---

# VLAN

## 🧾 Visão Geral

O recurso VLAN permite que múltiplas aplicações Discloud se comuniquem por uma rede privada isolada (container-para-container) sem expor serviços internos publicamente. Cenários típicos:

| Serviço        | Propósito                 | Exemplo                                  |
| -------------- | ------------------------- | ---------------------------------------- |
| API Backend    | Lógica de negócio         | App `api` chamando banco de dados        |
| Banco de Dados | Armazenamento persistente | Modelo ou container MongoDB / PostgreSQL |
| Cache          | Dados de baixa latência   | Instância Redis                          |

{% hint style="info" %}
O tráfego permanece dentro da infraestrutura Discloud. Nenhum ingresso público é criado para serviços acessados apenas via hostname privado.
{% endhint %}

***

## ⚙️ Configuração ([discloud.config](./))

Adicione as seguintes chaves a cada aplicação que deve participar da rede privada:

<pre class="language-properties" data-title="discloud.config"><code class="lang-properties"><a data-footnote-ref href="#user-content-fn-1"># ...</a>
NAME=Meu Servidor Mongo
VLAN=true
HOSTNAME=mymongoserver
#       |      ^     |
#       |      Nome da rede privada para esta aplicação
</code></pre>

| Chave      | Obrigatório | Descrição                                                       |
| ---------- | ----------- | --------------------------------------------------------------- |
| `VLAN`     | Sim         | Habilita rede privada para a aplicação                          |
| `HOSTNAME` | Recomendado | Alias de hostname personalizado para outras apps acessarem esta |

{% hint style="warning" %}
Se duas apps definirem o mesmo HOSTNAME, o comportamento é indefinido. Mantenha hostnames únicos e em minúsculas (letras, dígitos, hífens).
{% endhint %}

***

## 🧷 Exemplo: Serviço MongoDB + Backend

App de serviço:

{% code title="discloud.config" %}
```properties
NAME=Serviço Mongo
VLAN=true
HOSTNAME=mymongoserver
```
{% endcode %}

Código de conexão do backend:

{% tabs %}
{% tab title="TypeScript" %}
```typescript
import mongoose from "mongoose";

const uri = "mongodb://mymongoserver:27017/mydatabase";
//                            ^
//                            HOSTNAME do app de serviço Mongo

async function main() {
  try {
    await mongoose.connect(uri);
    console.log("Conectado ao MongoDB com sucesso");
  } catch (error) {
    console.error("Erro de conexão MongoDB:", error);
    process.exit(1);
  }
}

main();
```
{% endtab %}

{% tab title="Node (Driver Nativo)" %}
```javascript
import { MongoClient } from "mongodb";
const uri = "mongodb://mymongoserver:27017/mydatabase";
const client = new MongoClient(uri);
await client.connect();
console.log("Ping:", await client.db().command({ ping: 1 }));
```
{% endtab %}

{% tab title="Python" %}
```python
from pymongo import MongoClient
client = MongoClient('mongodb://mymongoserver:27017/mydatabase')
print(client.admin.command('ping'))
```
{% endtab %}
{% endtabs %}

{% hint style="info" %}
📌 **Certifique-se de expor as portas corretas no seu Dockerfile caso esteja usando um!**
{% endhint %}

***

## 🧵 Convenções de Hostname

| Regra       | Recomendação       |
| ----------- | ------------------ |
| Caracteres  | Apenas `a-z 0-9 -` |
| Comprimento | 1–25 caracteres    |

***

## 🛡️ Notas de Segurança

| Aspecto    | Detalhe                                                            |
| ---------- | ------------------------------------------------------------------ |
| Isolamento | Apenas apps que você hospeda com VLAN habilitado podem se alcançar |
| Exposição  | Nenhuma publicação automática de porta pública                     |
| Segredos   | Ainda armazene credenciais via variáveis de ambiente               |
| Princípio  | Desabilite VLAN em apps que não precisam de acessibilidade interna |

{% hint style="success" %}
Combine VLAN com credenciais de escopo de ambiente para menor privilégio.
{% endhint %}

[^1]: **Nota:** Os **`...`** apenas indicam a continuação de outras opções anteriores ou subsequentes que não são relevantes para mencionar nesta página.

---
description: >-
  Guia de autenticação para usar a API da Discloud (como obter e usar com
  segurança seu Token da API).
icon: key-skeleton
---

# Autenticação

{% hint style="info" %}
Todas as solicitações para a API da Discloud devem incluir um **Token da API** no cabeçalho `api-token`.

Se você ainda não tem um token, gere ou recupere-o no seu painel da Discloud. (Substitua esta nota pelo link exato do painel ou uma captura de tela.)
{% endhint %}

***

## ⚙️ Como Funciona

{% stepper %}
{% step %}
Você gera um [token](../../faq/general-questions/how-can-i-get-my-discloud-api-token.md) único vinculado à sua conta.
{% endstep %}

{% step %}
Para cada solicitação HTTP, inclua o cabeçalho: `api-token: SEU_TOKEN_AQUI`.
{% endstep %}

{% step %}
O token autentica e autoriza ações em nome da sua conta (nunca compartilhe-o).
{% endstep %}

{% step %}
Use o endpoint `/user` para validar rapidamente o token.
{% endstep %}
{% endstepper %}

***

## 📤 Enviando o Token

{% tabs %}
{% tab title="cURL" %}
```bash
curl -X GET \
  -H "api-token: $DISCLOUD_TOKEN" \
  https://api.discloud.app/v2/user
```
{% endtab %}

{% tab title="Node.js (fetch)" %}
```javascript
import fetch from "node-fetch";

async function getCurrentUser() {
  const res = await fetch("https://api.discloud.app/v2/user", {
    headers: { "api-token": process.env.DISCLOUD_TOKEN },
  });

  if (!res.ok) {
    console.error("Solicitação falhou:", res.status, await res.text());
    return;
  }
  const data = await res.json();
  console.log(data);
}
```
{% endtab %}

{% tab title="Node.js (discloud.app SDK)" %}
```javascript
// Instale primeiro: npm i discloud.app
const { discloud } = require("discloud.app");

discloud.login("DISCLOUD_API_TOKEN");

async function validateToken() {
  try {
    const user = await discloud.user.fetch();
    console.log("Usuário autenticado:", user);
  } catch (e) {
    console.error("Token inválido ou erro de rede:", e.message);
  }
}
```
{% endtab %}
{% endtabs %}

***

## 🛡 Protegendo o Token

{% hint style="warning" %}
Nunca commite seu token (ex. no Git). Armazene-o em variáveis de ambiente ([`.env`](../../faq/general-questions/em-andamento-arquivo-.env.md), segredos CI/CD, etc.).
{% endhint %}

📌 Melhores práticas:

* Use variáveis de ambiente em vez de codificar.
* Rotacione o token periodicamente (ex. a cada 90 dias).
* Revogue e regenere imediatamente se suspeitar de exposição.
* Restrinja quem pode acessar a infraestrutura onde a variável está armazenada.

***

## ⚡ Verificação Rápida do Token

Chame `/user` logo após definir a variável de ambiente. Se você receber HTTP 200 com dados do usuário, a autenticação está funcionando.

{% hint style="info" %}
Você também pode atualizar a localidade do usuário (ex. `en-US`) através de `/locale/{locale}` para validar outra rota autenticada.
{% endhint %}

***

## 📚 Referência dos Endpoints Relacionados

As operações abaixo requerem o cabeçalho `api-token`:

{% openapi-operation spec="api-endpoints-pt-v2" path="/user" method="get" %}
[OpenAPI api-endpoints-pt-v2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/735bdc862891ec3813ec832d01829f8a8758889f0a9a342771e83529bfae3299.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20251016%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20251016T081024Z&X-Amz-Expires=172800&X-Amz-Signature=1407237cff4a13d24cd1d9f2030a9d9d809dee1bd03d5757899d1db3304f24ce&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

{% openapi-operation spec="api-endpoints-pt-v2" path="/locale/{locale}" method="put" %}
[OpenAPI api-endpoints-pt-v2](https://4401d86825a13bf607936cc3a9f3897a.r2.cloudflarestorage.com/gitbook-x-prod-openapi/raw/735bdc862891ec3813ec832d01829f8a8758889f0a9a342771e83529bfae3299.yaml?X-Amz-Algorithm=AWS4-HMAC-SHA256&X-Amz-Content-Sha256=UNSIGNED-PAYLOAD&X-Amz-Credential=dce48141f43c0191a2ad043a6888781c%2F20251016%2Fauto%2Fs3%2Faws4_request&X-Amz-Date=20251016T081024Z&X-Amz-Expires=172800&X-Amz-Signature=1407237cff4a13d24cd1d9f2030a9d9d809dee1bd03d5757899d1db3304f24ce&X-Amz-SignedHeaders=host&x-amz-checksum-mode=ENABLED&x-id=GetObject)
{% endopenapi-operation %}

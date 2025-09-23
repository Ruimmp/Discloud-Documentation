---
description: >-
  Enable private networking between Discloud applications using VLAN and
  HOSTNAME in discloud.config.
icon: network-wired
---

# VLAN

## 🧾 Overview

The VLAN feature lets multiple Discloud applications communicate over an isolated private network (container-to-container) without exposing internal services publicly. Typical scenarios:

| Service     | Purpose            | Example                                    |
| ----------- | ------------------ | ------------------------------------------ |
| Backend API | Business logic     | `api` app calling database                 |
| Database    | Persistent storage | MongoDB / PostgreSQL template or container |
| Cache       | Low-latency data   | Redis instance                             |

{% hint style="info" %}
Traffic stays within the Discloud infrastructure. No public ingress is created for services accessed only via the private hostname.
{% endhint %}

***

## ⚙️ Configuration ([discloud.config](./))

Add the following keys to each application that should participate in the private network:

{% code title="discloud.config" %}
```properties
# ... other settings ...
VLAN=true
HOSTNAME=mymongoserver
#        |      ^
#        |      Unique private hostname
```
{% endcode %}

| Key        | Required    | Description                                            |
| ---------- | ----------- | ------------------------------------------------------ |
| `VLAN`     | Yes         | Enables private networking for the application         |
| `HOSTNAME` | Recommended | Custom hostname alias for other apps to reach this one |

{% hint style="warning" %}
If two apps set the same HOSTNAME, behavior is undefined. Keep hostnames unique and lowercase (letters, digits, hyphens).
{% endhint %}

***

## 🧷 Example: MongoDB Service + Backend

Service app:

{% code title="discloud.config" %}
```properties
NAME=Mongo Service
VLAN=true
HOSTNAME=mymongoserver
```
{% endcode %}

Backend connection code:

{% tabs %}
{% tab title="TypeScript" %}
```typescript
import mongoose from 'mongoose';

const uri = 'mongodb://mymongoserver:27017/mydatabase';
//                            ^
//                            HOSTNAME from Mongo service app

async function main() {
    try {
        await mongoose.connect(uri);
        console.log('Connected to MongoDB successfully');
    } catch (error) {
        console.error('MongoDB connection error:', error);
        process.exit(1);
    }
}

main();
```
{% endtab %}

{% tab title="Node (Native Driver)" %}
```javascript
import { MongoClient } from 'mongodb';
const uri = 'mongodb://mymongoserver:27017/mydatabase';
const client = new MongoClient(uri);
await client.connect();
console.log('Ping:', await client.db().command({ ping: 1 }));
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

***

## 🧵 Hostname Conventions

| Rule       | Recommendation   |
| ---------- | ---------------- |
| Characters | `a-z 0-9 -` only |
| Length     | 1–25 chars       |

***

## 🛡️ Security Notes

| Aspect    | Detail                                                      |
| --------- | ----------------------------------------------------------- |
| Isolation | Only apps you deploy with VLAN enabled can reach each other |
| Exposure  | No automatic public port publishing                         |
| Secrets   | Still store credentials via environment variables           |
| Principle | Disable VLAN on apps that do not need internal reachability |

{% hint style="success" %}
Combine VLAN with environment-scoped credentials for least privilege.
{% endhint %}

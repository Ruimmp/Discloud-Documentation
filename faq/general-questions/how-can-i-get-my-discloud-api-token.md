---
description: Learn what the Discloud API Token is and where to find it on the Dashboard.
icon: key
hidden: true
---

# How can I get my Discloud API Token?

## 🔑 What is the Discloud API Token?

Your **Discloud API Token** is a **personal, secret credential** that authenticates you to all Discloud developer surfaces:

- **REST API requests**
- **Official CLI**
- **VS Code Extension**
- **SDK / Libraries** (e.g. npm, Python)

It uniquely identifies your account, so **anyone with this token can act as you**. Treat it like a password.

---

## 📍 Where to Get It

Follow these steps to view (or copy) your token on the Dashboard:

{% stepper %}
{% step %}
Open the Dashboard: [https://discloud.com/dashboard](https://discloud.com/dashboard)
{% endstep %}

{% step %}
Click the **API Key** tab (top section of your profile area).

<figure><img src="../../.gitbook/assets/Dashboard-API.png" alt="Dashboard API Key tab"><figcaption><p>API Key location on the Dashboard</p></figcaption></figure>
{% endstep %}

{% step %}
Use the **Copy** button to place the token on your clipboard.
{% endstep %}
{% endstepper %}

> If the field is hidden, click the **eye icon** to reveal it. Use **Reset Token** only if you suspect compromise.

---

## 🛠 Using the Token

### ✅ Environment Variable (Recommended)

Store it in an environment variable rather than hard‑coding:

```bash
export DISCLOUD_TOKEN=YOUR_TOKEN_VALUE   # macOS / Linux
setx DISCLOUD_TOKEN YOUR_TOKEN_VALUE     # Windows (Persistent)
```

Then your tools / scripts can read `DISCOLOUD_TOKEN` (adjust if your environment or tooling expects a different variable name).

### 🌐 cURL / REST Example

```bash
curl -H "Authorization: YOUR_TOKEN_VALUE" \
		 -H "Accept: application/json" \
		 https://api.discloud.com/v2/user
```

### 🟨 Node.js (fetch / axios)

```js
import axios from "axios";

const token = process.env.DISCCLOUD_TOKEN || "<replace>"; // ensure you load from env

const api = axios.create({
  baseURL: "https://api.discloud.com/v2",
  headers: { Authorization: token },
});

const user = await api.get("/user");
console.log(user.data);
```

### 🐍 Python (requests)

```python
import os, requests

token = os.getenv("DISCCLOUD_TOKEN") or "<replace>"
resp = requests.get("https://api.discloud.com/v2/user", headers={"Authorization": token})
print(resp.json())
```

> Replace placeholder variable names as needed; always load from environment or a secure secret store.

---

## 🧪 Integrations That Use This Token

| Tool / Surface        | How It Uses the Token                                            |
| --------------------- | ---------------------------------------------------------------- |
| **CLI**               | Reads from prompt, config file, or env var to authorize commands |
| **VS Code Extension** | Authenticates to list, deploy, and manage apps                   |
| **SDKs / Libraries**  | Adds the token as `Authorization` header for each API call       |
| **Direct REST Calls** | You manually set the header in automation scripts                |

---

## 🔒 Security Best Practices

| Practice                                    | Why                                         |
| ------------------------------------------- | ------------------------------------------- |
| Keep it private (never share or screenshot) | Prevent account takeover                    |
| Do NOT commit to Git                        | Public repos are scanned by bots            |
| Use environment variables / secret managers | Centralized rotation & safer logs           |
| Rotate (Reset Token) if exposed             | Immediately invalidates old token           |
| Separate prod vs. personal contexts         | Avoid accidental actions from local scripts |

{% hint style="warning" %}
If you accidentally publish or paste your token somewhere public, **reset it immediately** on the Dashboard (API Key tab) and redeploy any services using the old one.
{% endhint %}

---

## ♻️ Resetting Your Token

Click **Reset Token** on the API Key tab if:

- You committed it to a repository
- You shared it in logs / screenshots / support tickets
- You suspect unauthorized use

After resetting:

1. Update local environment variables
2. Reconfigure CLI / extensions / deployed secrets
3. Redeploy any workflows that cached the old value

---

## ❓ Troubleshooting

| Issue                          | Fix                                                                                                  |
| ------------------------------ | ---------------------------------------------------------------------------------------------------- |
| Token returns 401 Unauthorized | Confirm header is exactly `Authorization: TOKEN_VALUE` (no Bearer prefix unless future docs specify) |
| Forgot where to find it        | Return to Dashboard → API Key tab                                                                    |
| Rotated token, old still used  | Restart tools / shells so new env var loads                                                          |
| Logged token in console        | Clear logs and rotate token (assume compromised)                                                     |

---

## ✅ Summary

- The API Token is your all‑purpose credential for Discloud developer tools.
- Access it via **Dashboard → API Key**.
- Store it securely (env vars) and never commit or expose it.
- Reset immediately if leaked.

Need more help? Visit the **FAQ section** or join the [Discloud Discord](https://discord.discloudbot.com/).

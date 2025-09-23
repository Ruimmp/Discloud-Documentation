---
description: >-
  Learn how to diagnose and resolve common issues with applications that fail to
  stay online on Discloud.
---

# Diagnosing Offline Applications

If your application **shuts down unexpectedly** on Discloud, it is important to analyze **what might be causing the issue**. This guide will help you **identify, debug, and resolve** common problems related to applications going offline.

***

## 🛑 **Common Application Behaviors & Causes**

When an application shuts down unexpectedly, the **behavior** can provide clues about the root cause.

{% stepper %}
{% step %}
Starts and immediately shuts down.

* Indicates a **critical issue** preventing proper initialization.
* Likely causes: **RAM limitations, missing dependencies, incorrect configurations, or startup code errors**.
{% endstep %}

{% step %}
Shuts down during a specific action.

* Happens when the application is **triggered by a particular command or event**.
* Likely causes: **Uncaught exceptions, high resource usage, or API failures**.
{% endstep %}

{% step %}
Goes offline after a few days (free plan).

* Could be related to **Discloud’s anti-ghost app policy** for free plans.
* Consider **upgrading to a paid plan** to keep applications online.
{% endstep %}
{% endstepper %}

***

## ⚠️ **Potential Causes & Fixes**

{% hint style="warning" %}
#### **Insufficient RAM**

If your application **exceeds its allocated memory**, it may be **forcefully shut down**.

✔ **Monitor RAM usage** and optimize your code.\
✔ Consider **increasing RAM** in your [`discloud.config`](../../configurations/discloud.config/) file.
{% endhint %}

{% hint style="warning" %}
#### **Code Errors & Exceptions**

Unhandled exceptions or **bugs in your code** can cause crashes.

✔ Check the **logs** for error messages.\
✔ **Test locally** before deploying to Discloud.
{% endhint %}

{% hint style="warning" %}
#### **Free Plan Limitations**

Discloud’s free plan **may suspend inactive applications** to free up resources.

✔ If your application **goes offline unexpectedly**, this could be the reason.\
✔ Consider [**upgrading to a paid plan**](https://discloud.com/plans) to keep it running.
{% endhint %}

***

## 🛠️ **Step-by-Step Debugging**

📌 **A common mistake developers make is saying:** _"It works on my machine but not on Discloud."_

Remember, **Discloud operates in a Linux environment**. Your application must be **adapted to run on the target environment**, not just your local machine.

***

## ⚡ **Fixing Applications That Shut Down Immediately**

If your application **starts and immediately shuts down**, it’s often due to:

{% stepper %}
{% step %}
Insufficient RAM.

* If the application uses more memory than allocated, Discloud **forcefully shuts it down**.
* Check your **RAM usage** and **optimize memory-intensive operations**.
{% endstep %}

{% step %}
Errors during initialization.

* Bugs in the **startup sequence** can **prevent the app from running properly**.
* Check for **missing dependencies**, incorrect **configurations**, or **uncaught errors** in the startup logic.
{% endstep %}
{% endstepper %}

***

## ❗ **Fixing Applications That Shut Down During a Specific Action**

If your application **stops running when a specific event or action is triggered**, follow these debugging steps:

{% stepper %}
{% step %}
Check the logs.

* Logs provide valuable insights into what caused the crash.
* Look for **error messages** related to that action.
{% endstep %}

{% step %}
Review the code handling that action.

* Check for **unhandled exceptions**, **invalid API responses**, or **database errors**.
* Ensure proper **error handling** is in place.
{% endstep %}

{% step %}
Monitor resource usage.

* Some actions **require more RAM** (e.g., playing music, processing images).
* If the action is resource-intensive, **consider increasing RAM allocation**.
{% endstep %}
{% endstepper %}

***

## 🎵 **Common Examples (Discord Applications)**

{% hint style="info" %}
#### **Music Bots**

If the bot **shuts down when playing music**, it could be due to:\
✔ **High RAM usage** → Optimize audio processing.\
✔ **Missing `ffmpeg`** → Add `ffmpeg` in [`APT`](../../configurations/discloud.config/apt.md) dependencies.\
✔ **API rate limits** → Check if you're hitting limits with the music provider.
{% endhint %}

{% hint style="info" %}
#### **Image Generation Bots**

* **Generating images consumes memory**.
* Ensure your bot has **sufficient RAM** and optimizes image processing code.
{% endhint %}

***

## 🛰️ **Check Discloud's Status**

If none of the above solutions resolve the issue, check the Discloud status page or the Discord channel for any reported system-wide issues. Temporary infrastructure problems could impact the availability of your application.

* [**Discloud Status Page**](https://status.discloud.app/)
* [**Discloud Discord Channel**](https://discord.com/channels/584490943034425391/694744729731989605)

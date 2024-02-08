---
description: >-
  https://portswigger.net/web-security/access-control/lab-multi-step-process-with-no-access-control-on-one-step
---

# Multi-step process with no access control on one step

<figure><img src="../../../.gitbook/assets/1 (7).png" alt=""><figcaption></figcaption></figure>

Let's login as the admin using the following credentials:

| Username      | Password |
| ------------- | -------- |
| administrator | admin    |

<figure><img src="../../../.gitbook/assets/2 (13).png" alt=""><figcaption></figcaption></figure>

Let's now promote the `carlos` user to admin.

<figure><img src="../../../.gitbook/assets/3 (13).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can view this request in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/4 (10).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification.&#x20;

Next, let's login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/5 (11).png" alt=""><figcaption></figcaption></figure>

Let's view the session cookie in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/6 (8).png" alt=""><figcaption></figcaption></figure>

We now have to replace the session cookie in the `Repeater` tab with the `wiener` user's session cookie.&#x20;

We also have to the set the `username` parameter to the following:

```
wiener
```

<figure><img src="../../../.gitbook/assets/7 (9).png" alt=""><figcaption></figcaption></figure>

Let's go check in the browser.

<figure><img src="../../../.gitbook/assets/8 (3).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/9 (3).png" alt=""><figcaption></figcaption></figure>

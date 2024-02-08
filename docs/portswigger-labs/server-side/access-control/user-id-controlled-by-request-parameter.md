---
description: >-
  https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter
---

# User ID controlled by request parameter

<figure><img src="../../../.gitbook/assets/1 (10).png" alt=""><figcaption></figcaption></figure>

Let's login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/2 (19).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can view this request by going to `Proxy > HTTP History`.

<figure><img src="../../../.gitbook/assets/3 (19).png" alt=""><figcaption></figcaption></figure>

We can see that the request contains a parameter called `id` which is set to `wiener`. Let's forward the request to the `Repeater` and set the `id` parameter to the following:

```
carlos
```

<figure><img src="../../../.gitbook/assets/4 (16).png" alt=""><figcaption></figcaption></figure>

We can now submit this API key through the browser.

<figure><img src="../../../.gitbook/assets/6 (14).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (15).png" alt=""><figcaption></figcaption></figure>

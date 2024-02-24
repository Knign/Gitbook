---
description: >-
  https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-data-leakage-in-redirect
---

# User ID controlled by request parameter with data leakage in redirect

<figure><img src="../../../.gitbook/assets/1 (152).png" alt=""><figcaption></figcaption></figure>

Let's login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/2 (17).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we will be able to view the request in `Proxy > HTTP History`.

<figure><img src="../../../.gitbook/assets/3 (17).png" alt=""><figcaption></figcaption></figure>

We can see that the URI contains the `id` parameter set to `wiener`.&#x20;

Let's forward it to the `Repeater` for further modification.&#x20;

Once in the `Repeater`, we can set the `id` parameter to the following and send the request:

```
carlos
```

<figure><img src="../../../.gitbook/assets/4 (14).png" alt=""><figcaption></figcaption></figure>

As we can see the response contains a 302 code. Which means that this is a redirection response.&#x20;

We can follow the redirection however it is not necessary since we have the API key. Let's submit the key.

<figure><img src="../../../.gitbook/assets/6 (12).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (13).png" alt=""><figcaption></figcaption></figure>

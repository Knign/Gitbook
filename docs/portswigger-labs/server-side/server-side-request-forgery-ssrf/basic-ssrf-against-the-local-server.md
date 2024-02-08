---
description: https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-localhost
---

# Basic SSRF against the local server

<figure><img src="../../../.gitbook/assets/1 (129).png" alt=""><figcaption></figcaption></figure>

Let's click on `View details`.

<figure><img src="../../../.gitbook/assets/2 (120).png" alt=""><figcaption></figcaption></figure>

If we click on `Check stock`, the application returns us the available units.&#x20;

We can now intercept this request in Burp Suite.

<figure><img src="../../../.gitbook/assets/4 (83).png" alt=""><figcaption></figcaption></figure>

Let's send it to the `Repeater` so that we can modify and forward the request.&#x20;

We can set the `stockApi` parameter to the following, so that the server return the content to us:

```
http://localhost/admin
```

<figure><img src="../../../.gitbook/assets/5 (69).png" alt=""><figcaption></figcaption></figure>

Let's send the request.

<figure><img src="../../../.gitbook/assets/6 (54).png" alt=""><figcaption></figcaption></figure>

The application returned the content of `/admin`.&#x20;

We can now set the `setAPI` parameter to the following:

```
http://localhost/admin/delete?username=carlos
```

This will cause the application to delete the `carlos` user on our behalf.

<figure><img src="../../../.gitbook/assets/7 (45).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/8 (33).png" alt=""><figcaption></figcaption></figure>

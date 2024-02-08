---
description: >-
  https://portswigger.net/web-security/access-control/lab-url-based-access-control-can-be-circumvented
---

# URL-based access control can be circumvented

<figure><img src="../../../.gitbook/assets/1 (8).png" alt=""><figcaption></figcaption></figure>

Let's try to access the admin panel.

<figure><img src="../../../.gitbook/assets/2 (14).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to `Proxy > HTTP History` to view the request.

<figure><img src="../../../.gitbook/assets/3 (14).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Repeater` for further modification.&#x20;

Once inside the `Repeater`, set the request URI to:

```
/
```

And add the following request header:

```
X-Original-URL: /admin
```

This header overrides the URI present in the original request.

<figure><img src="../../../.gitbook/assets/4 (11).png" alt=""><figcaption></figcaption></figure>

In order to delete the `carlos` user, we have to set the original URL to:

```
/?username=carlos
```

And modify the header to the following:

```
X-Original-Url: /admin/delete
```

<figure><img src="../../../.gitbook/assets/5 (12).png" alt=""><figcaption></figcaption></figure>

Let's go and check the panel through the browser.

<figure><img src="../../../.gitbook/assets/6 (9).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (10).png" alt=""><figcaption></figcaption></figure>

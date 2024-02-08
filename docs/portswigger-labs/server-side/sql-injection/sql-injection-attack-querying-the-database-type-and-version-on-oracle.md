---
description: >-
  https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-oracle
---

# SQL injection attack, querying the database type and version on Oracle

<figure><img src="../../../.gitbook/assets/1 (5).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Accessories`.

<figure><img src="../../../.gitbook/assets/2 (8).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (9).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Repeater` for further modification.&#x20;

Once in the `Repeater`, let's set the `category` parameter to the following:

```
' UNION SELECT 'test','test' FROM dual--
```

<figure><img src="../../../.gitbook/assets/4 (5).png" alt=""><figcaption></figcaption></figure>

Now that we know there are two columns, we can set the `category` parameter to the following:

```
' UNION SELECT BANNER, NULL FROM v$version--
```

<figure><img src="../../../.gitbook/assets/5 (6).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/6 (3).png" alt=""><figcaption></figcaption></figure>

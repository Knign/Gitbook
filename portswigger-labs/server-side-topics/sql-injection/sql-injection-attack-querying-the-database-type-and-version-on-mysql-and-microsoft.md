---
description: >-
  https://portswigger.net/web-security/sql-injection/examining-the-database/lab-querying-database-version-mysql-microsoft
---

# SQL injection attack, querying the database type and version on MySQL and Microsoft

<figure><img src="../../../.gitbook/assets/1 (4).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Accessories`.

<figure><img src="../../../.gitbook/assets/2 (7).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (8).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Repeater` for further modification.&#x20;

Once in the `Repeater`, let's set the `category` parameter to the following:

```
' UNION SELECT 'test','test'#
```

<figure><img src="../../../.gitbook/assets/4 (4).png" alt=""><figcaption></figcaption></figure>

Now that we know there are two columns, we can set the `category` parameter to the following:

```
' UNION SELECT `@@version`, NULL#
```

<figure><img src="../../../.gitbook/assets/5 (5).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/6 (2).png" alt=""><figcaption></figcaption></figure>

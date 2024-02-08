---
description: >-
  https://portswigger.net/web-security/sql-injection/union-attacks/lab-determine-number-of-columns
---

# SQL injection UNION attack, determining the number of columns returned by the query

<figure><img src="../../../.gitbook/assets/1 (161).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Accessories`.

<figure><img src="../../../.gitbook/assets/2 (143).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (125).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification.

Once in the `Repeater`, let's set the `category` parameter to the following:

```
UNION SELECT NULL--
```

<figure><img src="../../../.gitbook/assets/4 (106).png" alt=""><figcaption></figcaption></figure>

Since the application returns an error, we know that the number of columns in the current query is more than 1.

Let's try for two columns:

```
UNION SELECT NULL,NULL--
```

<figure><img src="../../../.gitbook/assets/5 (89).png" alt=""><figcaption></figcaption></figure>

The application again returns an error.

Let's try for three columns:

```
UNION SELECT NULL,NULL,NULL--
```

<figure><img src="../../../.gitbook/assets/6 (75).png" alt=""><figcaption></figcaption></figure>

The application no longer throws an error which means that there are 3 columns in the current query.

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (58).png" alt=""><figcaption></figcaption></figure>

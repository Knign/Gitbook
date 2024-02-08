---
description: https://portswigger.net/web-security/sql-injection/cheat-sheet
---

# SQL injection UNION attack, retrieving multiple values in a single column

<figure><img src="../../../.gitbook/assets/1 (164).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Accessories`.

<figure><img src="../../../.gitbook/assets/2 (146).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (128).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification.

Once in the `Repeater`, let's set the `category` parameter to the following:

```
' UNION SELECT NULL--
```

<figure><img src="../../../.gitbook/assets/4 (109).png" alt=""><figcaption></figcaption></figure>

Since the application returns an error, we know that the number of columns in the current query is more than 1. Let's set the `category` parameter to the following:

```
' UNION SELECT NULL,NULL--
```

<figure><img src="../../../.gitbook/assets/5 (92).png" alt=""><figcaption></figcaption></figure>

Now that we know the current query has two columns, we can retrieve the usernames and password from the `username` and `password` columns respectively.

```
' UNION SELECT NULL,username||':'||password FROM users--
```

The `||` characters are used to concatenate strings together. So we are essentially dumping the username and password in the same column in the following format:

```
username:password
```

<figure><img src="../../../.gitbook/assets/6 (78).png" alt=""><figcaption></figcaption></figure>

We can now login as the admin using the following credentials:

| Username      | Password             |
| ------------- | -------------------- |
| administrator | fq4yq6966ve3gff4iz65 |

<figure><img src="../../../.gitbook/assets/7 (61).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/8 (45).png" alt=""><figcaption></figcaption></figure>

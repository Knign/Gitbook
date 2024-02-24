---
description: >-
  https://portswigger.net/web-security/sql-injection/union-attacks/lab-retrieve-data-from-other-tables
---

# SQL injection UNION attack, retrieving data from other tables

<figure><img src="../../../.gitbook/assets/1 (163).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Gifts`.

<figure><img src="../../../.gitbook/assets/2 (145).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (127).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification.

Once in the `Repeater`, let's set the `category` parameter to the following:

```
' UNION SELECT 'test'--
```

<figure><img src="../../../.gitbook/assets/4 (108).png" alt=""><figcaption></figcaption></figure>

Since the application returns an error, we know that the number of columns in the current query is more than 1.

Let's set the `category` parameter to the following:

```
' UNION SELECT 'test', 'test'--
```

<figure><img src="../../../.gitbook/assets/5 (91).png" alt=""><figcaption></figcaption></figure>

Now that we know the current query has two columns, we can retrieve the usernames and password from the `username` and `password` columns respectively.

```
' UNION SELECT username, password FROM users--
```

<figure><img src="../../../.gitbook/assets/6 (77).png" alt=""><figcaption></figcaption></figure>

We can now login as the admin using the following credentials:

| Username      | Password             |
| ------------- | -------------------- |
| administrator | 21tpnvx8ho5pyej8z6sy |

<figure><img src="../../../.gitbook/assets/7 (60).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/88.png" alt=""><figcaption></figcaption></figure>

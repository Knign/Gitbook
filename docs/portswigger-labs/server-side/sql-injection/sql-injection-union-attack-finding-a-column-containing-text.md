---
description: >-
  https://portswigger.net/web-security/sql-injection/union-attacks/lab-find-column-containing-text
---

# SQL injection UNION attack, finding a column containing text

<figure><img src="../../../.gitbook/assets/1 (162).png" alt=""><figcaption></figcaption></figure>

Let's filter for `Accessories`.

<figure><img src="../../../.gitbook/assets/2 (144).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view this request.

<figure><img src="../../../.gitbook/assets/3 (126).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification.

Once in the `Repeater`, let's set the `category` parameter to the following:

```
UNION SELECT NULL--
```

<figure><img src="../../../.gitbook/assets/4 (107).png" alt=""><figcaption></figcaption></figure>

Since the application returns an error, we know that the number of columns in the current query is more than 1.

Let's try for two columns:

```
UNION SELECT NULL,NULL--
```

<figure><img src="../../../.gitbook/assets/5 (90).png" alt=""><figcaption></figcaption></figure>

The application again returns an error.

Let's try for three columns:

```
UNION SELECT NULL,NULL,NULL--
```

<figure><img src="../../../.gitbook/assets/6 (76).png" alt=""><figcaption></figcaption></figure>

The application no longer throws an error which means that there are 3 columns in the current query.

Now let's change one column to a string instead of `NULL` and observe the behaviour.

```
UNION SELECT 'test',NULL,NULL--
```

<figure><img src="../../../.gitbook/assets/7 (59).png" alt=""><figcaption></figcaption></figure>

That tells us that the first column is not compatible with string data.

Let's move on to the next column.

```
UNION SELECT NULL,'test',NULL--
```

<figure><img src="../../../.gitbook/assets/8 (44).png" alt=""><figcaption></figcaption></figure>

We can see that the second column is compatible with string data.

Now all we have to do is replace `test` with the string that we have to make the database retrieve.

<figure><img src="../../../.gitbook/assets/9 (33).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/10 (30).png" alt=""><figcaption></figcaption></figure>

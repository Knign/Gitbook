---
description: >-
  https://portswigger.net/web-security/access-control/lab-referer-based-access-control
---

# Referer-based access control

<figure><img src="../../../.gitbook/assets/1 (6).png" alt=""><figcaption></figcaption></figure>

We can login as the admin using the following credentials:

| Username      | Password |
| ------------- | -------- |
| administrator | admin    |

<figure><img src="../../../.gitbook/assets/2 (12).png" alt=""><figcaption></figcaption></figure>

Let's go to the admin panel and upgrade the `carlos` user.

<figure><img src="../../../.gitbook/assets/3 (12).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to the `Proxy > HTTP History` tab to view the request.

<figure><img src="../../../.gitbook/assets/4 (9).png" alt=""><figcaption></figcaption></figure>

Notice that the request contains the `Refered` header set to the following:

```
https://0ab4000404f019d8885f257200e0002f.web-security-academy.net/admin
```

That tells the server that the request is coming from the `/admin` page which can only be accessed by the administrator.

Let's forward this request to the `Repeater` for further modification.

Next, let's logout and login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/5 (10).png" alt=""><figcaption></figcaption></figure>

We now have to replace the session cookie in the `Repeater` tab with the `wiener` user's session cookie and set the `username` parameter to the following:

```
wiener
```

<figure><img src="../../../.gitbook/assets/6 (7).png" alt=""><figcaption></figcaption></figure>

Since we included the `Referer` header, the server upgraded our user.

Let's check in the browser.

<figure><img src="../../../.gitbook/assets/7 (8).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/8 (2).png" alt=""><figcaption></figcaption></figure>

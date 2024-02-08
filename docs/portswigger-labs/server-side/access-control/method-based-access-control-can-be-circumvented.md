---
description: >-
  https://portswigger.net/web-security/access-control/lab-method-based-access-control-can-be-circumvented
---

# Method-based access control can be circumvented

<figure><img src="../../../.gitbook/assets/1 (155).png" alt=""><figcaption></figcaption></figure>

Let's login as the admin using the following credentials:

| Username      | Password |
| ------------- | -------- |
| administrator | admin    |

<figure><img src="../../../.gitbook/assets/2 (15).png" alt=""><figcaption></figcaption></figure>

We can now upgrade the `carlos` user to admin.

<figure><img src="../../../.gitbook/assets/3 (15).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we will be able to view this request in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/4 (12).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification.&#x20;

Next, let's log out and log back in using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/5 (13).png" alt=""><figcaption></figcaption></figure>

We can go to the `Proxy > HTTP History` tab to get the session cookie.

<figure><img src="../../../.gitbook/assets/6 (10).png" alt=""><figcaption></figcaption></figure>

Now, let's go back to the `Repeater` tab and change the request method to POST.

<figure><img src="../../../.gitbook/assets/7 (11).png" alt=""><figcaption></figcaption></figure>

Next, we have to replace the session cookie with the one from the `wiener` user's request. We also have to set the `username` parameter to the following:

```
wiener
```

<figure><img src="../../../.gitbook/assets/8 (4).png" alt=""><figcaption></figcaption></figure>

Let's go and check the browser.

<figure><img src="../../../.gitbook/assets/9 (4).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/10 (3).png" alt=""><figcaption></figcaption></figure>

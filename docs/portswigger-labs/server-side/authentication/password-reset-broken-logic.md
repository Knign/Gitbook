---
description: >-
  https://portswigger.net/web-security/authentication/other-mechanisms/lab-password-reset-broken-logic
---

# Password reset broken logic

<figure><img src="../../../.gitbook/assets/1 (16).png" alt=""><figcaption></figcaption></figure>

Let's click on `My account`.

<figure><img src="../../../.gitbook/assets/2 (25).png" alt=""><figcaption></figcaption></figure>

Click on `Forgot password?`. Then enter the `wiener` username.

<figure><img src="../../../.gitbook/assets/3 (26).png" alt=""><figcaption></figcaption></figure>

Next, we have to click on `Email client` in order to check our emails.

<figure><img src="../../../.gitbook/assets/5 (22).png" alt=""><figcaption></figcaption></figure>

Let's click on the link provided to us to reset our password.

<figure><img src="../../../.gitbook/assets/6 (21).png" alt=""><figcaption></figcaption></figure>

We can enter any password. Since we are proxying the traffic through Burp Suite, we can view this request in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/7 (20).png" alt=""><figcaption></figcaption></figure>

We can forward this request to the `Repeater` so that we can modify it.&#x20;

Once in the `Repeater` tab, let's remove the `temp-forgot-password-token` parameter from the URI as well as the POST data field and send the request to the server.

<figure><img src="../../../.gitbook/assets/8 (10).png" alt=""><figcaption></figcaption></figure>

We can see that our password has been changed even though we did not include the token, This means that the server sets the token but does not validate it.

Let's set the `username` field to the following and resend the request:

```
carlos
```

<figure><img src="../../../.gitbook/assets/9 (9).png" alt=""><figcaption></figcaption></figure>

Now we can login using the following credentials:

| Username | Password |
| -------- | -------- |
| carlos   | password |

<figure><img src="../../../.gitbook/assets/11 (2).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/12 (8).png" alt=""><figcaption></figcaption></figure>

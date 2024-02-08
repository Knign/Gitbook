---
description: >-
  https://portswigger.net/web-security/access-control/lab-user-role-controlled-by-request-parameter
---

# User role controlled by request parameter

<figure><img src="../../../.gitbook/assets/1 (150).png" alt=""><figcaption></figcaption></figure>

We can login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/2 (140).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can see this request in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/3 (122).png" alt=""><figcaption></figcaption></figure>

As we can see, the response sets an `Admin` cookie to `false`.&#x20;

In the next request, we can see that the cookie is used in the header.

<figure><img src="../../../.gitbook/assets/4 (103).png" alt=""><figcaption></figcaption></figure>

Let's go into the browser `Developer Tools > Storage` and set the `Admin` cookie to `true`.

<figure><img src="../../../.gitbook/assets/8 (43).png" alt=""><figcaption></figcaption></figure>

We can now refresh the page.

<figure><img src="../../../.gitbook/assets/6 (72).png" alt=""><figcaption></figcaption></figure>

We now have access to the admin panel.

<figure><img src="../../../.gitbook/assets/7 (56).png" alt=""><figcaption></figcaption></figure>

Let's delete the `carlos` user.

<figure><img src="../../../.gitbook/assets/9 (32).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/10 (29).png" alt=""><figcaption></figcaption></figure>

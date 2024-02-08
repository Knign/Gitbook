---
description: >-
  https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-unpredictable-user-ids
---

# User ID controlled by request parameter, with unpredictable user IDs

<figure><img src="../../../.gitbook/assets/1 (9).png" alt=""><figcaption></figcaption></figure>

We can login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/2 (18).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can go to `Proxy > HTTP History` in order to view the request.

<figure><img src="../../../.gitbook/assets/3 (18).png" alt=""><figcaption></figcaption></figure>

As we can see, the request contains an `id` parameter. In order to access the `carlos` user's API key we will first need to find his GUID.&#x20;

First let's forward this request to the `Repeater` for later modification.&#x20;

Then let's look for some post written by the `carlos` user.

<figure><img src="../../../.gitbook/assets/4 (15).png" alt=""><figcaption></figcaption></figure>

We can now view the user's profile.

<figure><img src="../../../.gitbook/assets/5 (15).png" alt=""><figcaption></figcaption></figure>

Let's read this request in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/6 (13).png" alt=""><figcaption></figcaption></figure>

Now that we have the GUID, we can go to the `Repeater` and set the `id` parameter to the `carlos` user's GUID and send the request.

<figure><img src="../../../.gitbook/assets/7 (14).png" alt=""><figcaption></figcaption></figure>

Let's submit the API key.

<figure><img src="../../../.gitbook/assets/8 (6).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/9 (5).png" alt=""><figcaption></figcaption></figure>

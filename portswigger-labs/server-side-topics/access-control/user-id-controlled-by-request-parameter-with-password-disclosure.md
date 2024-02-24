---
description: >-
  https://portswigger.net/web-security/access-control/lab-user-id-controlled-by-request-parameter-with-password-disclosure
---

# User ID controlled by request parameter with password disclosure

<figure><img src="../../../.gitbook/assets/1 (153).png" alt=""><figcaption></figcaption></figure>

Let's login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/2 (16).png" alt=""><figcaption></figcaption></figure>

We can see that the password is included in the input field for resetting the password. However this password is hidden.&#x20;

Let's view this in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/3 (16).png" alt=""><figcaption></figcaption></figure>

We can clearly see the value of the password. We can view the administrator's password in a similar manner. Let's forward the request to the `Repeater` and set the `id` parameter to the following:

```
administrator
```

<figure><img src="../../../.gitbook/assets/4 (13).png" alt=""><figcaption></figcaption></figure>

Now we can login as the administrator using the following credentials:

| Username      | Password             |
| ------------- | -------------------- |
| administrator | eg9yjeq3lztdlfb0bnay |

<figure><img src="../../../.gitbook/assets/5 (14).png" alt=""><figcaption></figcaption></figure>

We now have access to the admin panel.

<figure><img src="../../../.gitbook/assets/6 (11).png" alt=""><figcaption></figcaption></figure>

Let's delete the `carlos` user.

<figure><img src="../../../.gitbook/assets/7 (12).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/8 (5).png" alt=""><figcaption></figcaption></figure>

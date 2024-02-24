---
description: >-
  https://portswigger.net/web-security/access-control/lab-user-role-can-be-modified-in-user-profile
---

# User role can be modified in user profile

<figure><img src="../../../.gitbook/assets/1 (151).png" alt=""><figcaption></figcaption></figure>

Let's login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

Once logged in, we can change our email address.

<figure><img src="../../../.gitbook/assets/2 (141).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can view the request by going to `Proxy > HTTP History`.

<figure><img src="../../../.gitbook/assets/3 (123).png" alt=""><figcaption></figcaption></figure>

We can see that the response contains the following key:value pair:

```
"roleid":1
```

Let's forward this request to the `Repeater` and include the key:value pair in the body of the request.

<figure><img src="../../../.gitbook/assets/4 (104).png" alt=""><figcaption></figcaption></figure>

Now we can access tot admin panel using our browser.

<figure><img src="../../../.gitbook/assets/5 (87).png" alt=""><figcaption></figcaption></figure>

Let's delete the `carlos` user.

<figure><img src="../../../.gitbook/assets/6 (73).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (57).png" alt=""><figcaption></figcaption></figure>

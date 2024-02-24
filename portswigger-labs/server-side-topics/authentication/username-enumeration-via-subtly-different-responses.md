---
description: >-
  https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-subtly-different-responses
---

# Username enumeration via subtly different responses

<figure><img src="../../../.gitbook/assets/1 (142).png" alt=""><figcaption></figcaption></figure>

Let's click on the `My account` button.

<figure><img src="../../../.gitbook/assets/2 (135).png" alt=""><figcaption></figcaption></figure>

We are proxying the traffic through Burp Suite. Therefore we can find the login request in the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/3 (116).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Intruder`. Once in the `Intruder`, let's set the payload field on the `username` parameter.

<figure><img src="../../../.gitbook/assets/4 (98).png" alt=""><figcaption></figcaption></figure>

Now we have to set the payload type to `Simple list`. Once that is done, we can paste the usernames provided to us here in the `Payloads settings` section.

<figure><img src="../../../.gitbook/assets/5 (82).png" alt=""><figcaption></figcaption></figure>

Next, in the `Intruder > Settings` tab, we have to go to the `Grep - Extract` section and clink on the `Add` button.

<figure><img src="../../../.gitbook/assets/6 (66).png" alt=""><figcaption></figcaption></figure>

Inside the pop-up, select the following string from the response:

```
Invalid username or password.
```

<figure><img src="../../../.gitbook/assets/7 (52).png" alt=""><figcaption></figcaption></figure>

We can now start the attack.

<figure><img src="../../../.gitbook/assets/8 (40).png" alt=""><figcaption></figcaption></figure>

As we can see, the request with the `username` parameter set to `apps` return a slightly different response, without the full stop. This means that the username worked which triggered different behaviour.&#x20;

Now, we have to fuzz the password. With the `username` parameter set to `apps`, add the payload filed to the `password` parameter.

<figure><img src="../../../.gitbook/assets/9 (30).png" alt=""><figcaption></figcaption></figure>

In the `Payloads` tab, set the type to `Simple list` and paste the passwords provided to us.

<figure><img src="../../../.gitbook/assets/10 (27).png" alt=""><figcaption></figcaption></figure>

Let's start the attack.

<figure><img src="../../../.gitbook/assets/11 (13).png" alt=""><figcaption></figcaption></figure>

The request where the `password` parameter was set to `1111` returned a 302 response. Now we can login using the fuzzed credentials:

| Username | Password |
| -------- | -------- |
| apps     | 1111     |

<figure><img src="../../../.gitbook/assets/12 (9).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/13 (10).png" alt=""><figcaption></figcaption></figure>

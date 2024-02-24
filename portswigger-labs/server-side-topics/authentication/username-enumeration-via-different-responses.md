---
description: >-
  https://portswigger.net/web-security/authentication/password-based/lab-username-enumeration-via-different-responses
---

# Username enumeration via different responses

<figure><img src="../../../.gitbook/assets/1 (140).png" alt=""><figcaption></figcaption></figure>

We can click on `My Account` in order to login.

<figure><img src="../../../.gitbook/assets/2 (133).png" alt=""><figcaption></figcaption></figure>

We can view the `Proxy > HTTP History` in Burp Suite to view this request.

<figure><img src="../../../.gitbook/assets/3 (114).png" alt=""><figcaption></figcaption></figure>

Let's forward it to the `Intruder` and add a payload field to the `username` parameter.

<figure><img src="../../../.gitbook/assets/4 (96).png" alt=""><figcaption></figcaption></figure>

Next we can go to the `Payloads` tab and set the `Payload type` to `Simple list`. Once that is done, we can paste the usernames provided to us here in the `Payloads settings` section.

<figure><img src="../../../.gitbook/assets/5 (80).png" alt=""><figcaption></figcaption></figure>

Let's start the attack.

<figure><img src="../../../.gitbook/assets/6 (65).png" alt=""><figcaption></figcaption></figure>

We can observe that the request with `username` set to `analyzer` returned a different response than the others. This is because this username was correct whereas the others weren't.

&#x20;Now we can craft another attack by setting the `username` parameter to `carlos` and adding a payload field to the `password` parameter.

<figure><img src="../../../.gitbook/assets/7 (51).png" alt=""><figcaption></figcaption></figure>

In the `Payloads` tab we will again be using a `Simple list`. Let's paste the passwords provided to use here in the `Paeyloads section`.

<figure><img src="../../../.gitbook/assets/8 (39).png" alt=""><figcaption></figcaption></figure>

We are now set to start the attack.

<figure><img src="../../../.gitbook/assets/9 (29).png" alt=""><figcaption></figcaption></figure>

As we can see, the request with the `password` set to `1234567890` gives a `302` response. Now that we know what the username and password are, let's login.

| Username | Password   |
| -------- | ---------- |
| analyzer | 1234567890 |

<figure><img src="../../../.gitbook/assets/10 (26).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/11 (12).png" alt=""><figcaption></figcaption></figure>

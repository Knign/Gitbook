---
description: >-
  https://portswigger.net/web-security/ssrf/lab-basic-ssrf-against-backend-system
---

# Basic SSRF against another back-end system

<figure><img src="../../../.gitbook/assets/1 (128).png" alt=""><figcaption></figcaption></figure>

Let's check out the stock.

<figure><img src="../../../.gitbook/assets/2 (119).png" alt=""><figcaption></figcaption></figure>

We can intercept the request using Burpsuite and send it to the `Intruder`.

<figure><img src="../../../.gitbook/assets/3 (101).png" alt=""><figcaption></figcaption></figure>

We do not know the IP address of the back-end system. We can find it by fuzzing all the IP addresses in the network.

Let's set the `stockApi` parameter to the following:

```
http://192.168.0.X:8080/admin
```

For the payload, the type is `Numbers` from 1-255.

<figure><img src="../../../.gitbook/assets/4 (82).png" alt=""><figcaption></figcaption></figure>

Let's start the attack.&#x20;

After some time we can see the only request that returned a `200` response code is the one where the last field is `59`.

<figure><img src="../../../.gitbook/assets/5 (68).png" alt=""><figcaption></figcaption></figure>

This means that the IP address of the backend system is `192.168.0.59`.

Finally, we have to send the request to the `Repeater` and set the `stockAPI` parameter to the following:

```
http://192.168.0.159:8080/admin/delete?username=carlos
```

<figure><img src="../../../.gitbook/assets/6 (53).png" alt=""><figcaption></figcaption></figure>

We have solved the lab

<figure><img src="../../../.gitbook/assets/7 (44).png" alt=""><figcaption></figcaption></figure>

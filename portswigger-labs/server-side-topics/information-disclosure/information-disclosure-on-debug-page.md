---
description: >-
  https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-on-debug-page
---

# Information disclosure on debug page

<figure><img src="../../../.gitbook/assets/1 (148).png" alt=""><figcaption></figcaption></figure>

If we go to `Target > Site map`, we can see a request for `/cgi-bin/phpinfo.php`.&#x20;

Let's forward that request to the `Repeater` and send it.&#x20;

When the response is returned to us, we can search for the following string:

```
SECRET_KEY
```

<figure><img src="../../../.gitbook/assets/3 (120).png" alt=""><figcaption></figcaption></figure>

As we can see, the secret is revealed by the server in the response.&#x20;

We can now submit the secret key as the answer:

```
08py31h0x95q3hfiieipk0q5i3xch7d9
```

<figure><img src="../../../.gitbook/assets/4 (101).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/5 (20).png" alt=""><figcaption></figcaption></figure>

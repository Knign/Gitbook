---
description: >-
  https://portswigger.net/web-security/access-control/lab-insecure-direct-object-references
---

# Insecure direct object references

<figure><img src="../../../.gitbook/assets/1 (154).png" alt=""><figcaption></figcaption></figure>

Let's start the live chat.

<figure><img src="../../../.gitbook/assets/2 (142).png" alt=""><figcaption></figcaption></figure>

We can now download this chat by clicking on the `View transcript` button. Since we are proxying the traffic through Burp Suite, we will be able to see the request in the `Proxy > HTTP History`.

<figure><img src="../../../.gitbook/assets/2.2.png" alt=""><figcaption></figcaption></figure>

We are being redirected, let's view the next request.

<figure><img src="../../../.gitbook/assets/3 (124).png" alt=""><figcaption></figcaption></figure>

As we can see, our entire chat log is saved. Let's forward this request to the `Repeater` for further modification. Once in the `Repeater`, change the GET URI to the following:

```
/download-tanscript/2.txt
```

<figure><img src="../../../.gitbook/assets/4 (105).png" alt=""><figcaption></figcaption></figure>

This causes the application to give the transcripts of another user's chat. We can now try to login to the `carlos` user's account using the following credentials:

| Username | Password             |
| -------- | -------------------- |
| carlos   | z7yiqtqjuttawu19dlxw |

<figure><img src="../../../.gitbook/assets/5 (88).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/6 (74).png" alt=""><figcaption></figcaption></figure>

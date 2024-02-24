---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/stored/lab-html-context-nothing-encoded
---

# Stored XSS into HTML context with nothing encoded

<figure><img src="../../../.gitbook/assets/1 (166).png" alt=""><figcaption></figcaption></figure>

Let's comment the following payload below the post:

```
<script>alert("1");</script>
```

Since this payload is stored on the page in the form of a comment it will be executed for every user that visits the page.

<figure><img src="../../../.gitbook/assets/2 (4).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/3 (5).png" alt=""><figcaption></figcaption></figure>

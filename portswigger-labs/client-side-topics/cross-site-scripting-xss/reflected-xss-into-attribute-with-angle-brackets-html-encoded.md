---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/contexts/lab-attribute-angle-brackets-html-encoded
---

# Reflected XSS into attribute with angle brackets HTML-encoded

<figure><img src="../../../.gitbook/assets/1 (169).png" alt=""><figcaption></figcaption></figure>

Let's insert the following payload in the search field:

```
test_payload
```

We can now open `Left CLick > Inspect` to open the developer tools and search our payload.

<figure><img src="../../../.gitbook/assets/2 (150).png" alt=""><figcaption></figcaption></figure>

We can see that our `test_payload` has been inserted into the `value` attribute of the `<input>` tag.

In order to generate an alert, we need to first escape the `value` attribute and than add an `onmouseover` event attribute.

```
test_payload" onmouseover="alert(1)
```

The alert will be displayed only when we hover over the input field with our mouse.

<figure><img src="../../../.gitbook/assets/3 (132).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/4 (113).png" alt=""><figcaption></figcaption></figure>

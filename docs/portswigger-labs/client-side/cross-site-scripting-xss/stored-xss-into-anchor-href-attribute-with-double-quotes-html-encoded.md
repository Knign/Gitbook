---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/contexts/lab-href-attribute-double-quotes-html-encoded
---

# Stored XSS into anchor href attribute with double quotes HTML-encoded

<figure><img src="../../../.gitbook/assets/1 (170).png" alt=""><figcaption></figcaption></figure>

Let's go and comment the following under the post.

<figure><img src="../../../.gitbook/assets/2 (151).png" alt=""><figcaption></figcaption></figure>

We can now open `Left CLick > Inspect` to open the developer tools and search our `website.com` payload.

<figure><img src="../../../.gitbook/assets/3 (133).png" alt=""><figcaption></figcaption></figure>

As we can see, it is being inserted in the `href` attribute of the `<a>` tag.

In order to solve the lab, we have to use the following payload in the `Website` input field:

```
javascript:alert("1");
```

<figure><img src="../../../.gitbook/assets/4 (114).png" alt=""><figcaption></figcaption></figure>

Let's verify if the payload has been inserted properly.

<figure><img src="../../../.gitbook/assets/5 (94).png" alt=""><figcaption></figcaption></figure>

Now, if we click on the `<a>` tag link, the Javascript will be executed, generating an alert.

<figure><img src="../../../.gitbook/assets/6 (80).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (62).png" alt=""><figcaption></figcaption></figure>

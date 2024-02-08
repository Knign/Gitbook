---
description: >-
  https://portswigger.net/web-security/access-control/lab-unprotected-admin-functionality
---

# Unprotected admin functionality

<figure><img src="../../../.gitbook/assets/1 (12).png" alt=""><figcaption></figcaption></figure>

We can go to the `/robots.txt` file to check is any pages are disallowed for web crawler.

<figure><img src="../../../.gitbook/assets/2 (21).png" alt=""><figcaption></figcaption></figure>

As we can see, the `/administrator-panel` page is blocked. Let's visit it through the browser.

<figure><img src="../../../.gitbook/assets/3 (21).png" alt=""><figcaption></figcaption></figure>

We can now delete the `carlos` user.

<figure><img src="../../../.gitbook/assets/4 (18).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/5 (18).png" alt=""><figcaption></figcaption></figure>

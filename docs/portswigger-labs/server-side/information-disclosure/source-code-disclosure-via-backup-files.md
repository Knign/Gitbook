---
description: >-
  https://portswigger.net/web-security/information-disclosure/exploiting/lab-infoleak-via-backup-files
---

# Source code disclosure via backup files

<figure><img src="../../../.gitbook/assets/1 (149).png" alt=""><figcaption></figcaption></figure>

We can go to the `/robots.txt` page to see what pages are blocked for web crawlers.

<figure><img src="../../../.gitbook/assets/2 (139).png" alt=""><figcaption></figcaption></figure>

We can see that the `/backup` are blocked. Let's visit it.

<figure><img src="../../../.gitbook/assets/3 (121).png" alt=""><figcaption></figcaption></figure>

Let's go the file.

<figure><img src="../../../.gitbook/assets/4 (102).png" alt=""><figcaption></figcaption></figure>

As we can see there is a hardcoded password there.

```
qyb8rfjmzv1edk56w3dwmaom3o505wvy
```

We can submit this password as the answer.

<figure><img src="../../../.gitbook/assets/5 (86).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/6 (71).png" alt=""><figcaption></figcaption></figure>

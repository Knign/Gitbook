---
description: >-
  https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-inconsistent-security-controls
---

# Inconsistent security controls

<figure><img src="../../../.gitbook/assets/1 (143).png" alt=""><figcaption></figcaption></figure>

We can go to the `Target > Site Map` tab in Burp Suite in order to see the domain.

<figure><img src="../../../.gitbook/assets/2 (136).png" alt=""><figcaption></figcaption></figure>

Let's left click on the domain present and then `Engagement tools > Discover content`.

<figure><img src="../../../.gitbook/assets/3 (117).png" alt=""><figcaption></figcaption></figure>

That would tell us that there is a directory called `/admin`. Alternatively, we can also directory fuzzing tools. Let's visit the `/admin` page through the browser.

<figure><img src="../../../.gitbook/assets/4 (99).png" alt=""><figcaption></figcaption></figure>

As we can see, the admin page is only accessible to "DontWannaCry" users.&#x20;

Let's `Register` our user using our assigned email address.

<figure><img src="../../../.gitbook/assets/5 (83).png" alt=""><figcaption></figcaption></figure>

Next, we can go to the `Email client` and click our registration email.

<figure><img src="../../../.gitbook/assets/6 (67).png" alt=""><figcaption></figcaption></figure>

Then, we can login to our created account through the `My account` tab.

<figure><img src="../../../.gitbook/assets/7 (53).png" alt=""><figcaption></figcaption></figure>

Once inside, we get the option to change our email. Let's set it the following:

```
attacker@dontwannacry.com
```

<figure><img src="../../../.gitbook/assets/8 (41).png" alt=""><figcaption></figcaption></figure>

Once we update our email, the admin panel becomes accessible to us.

<figure><img src="../../../.gitbook/assets/9 (31).png" alt=""><figcaption></figcaption></figure>

Let's go inside the admin panel.

<figure><img src="../../../.gitbook/assets/10 (28).png" alt=""><figcaption></figcaption></figure>

We have to delete the `carlos` user.

<figure><img src="../../../.gitbook/assets/11 (14).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/12 (10).png" alt=""><figcaption></figcaption></figure>

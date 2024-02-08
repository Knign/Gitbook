---
description: >-
  https://portswigger.net/web-security/logic-flaws/examples/lab-logic-flaws-flawed-enforcement-of-business-rules
---

# Flawed enforcement of business rules

<figure><img src="../../../.gitbook/assets/1 (144).png" alt=""><figcaption></figcaption></figure>

We have to login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

At the top of the page, we an see the following code:

```
NEWCUST5
```

If we scroll to the bottom, there is a newsletter that we can sign up for.

<figure><img src="../../../.gitbook/assets/2 (137).png" alt=""><figcaption></figcaption></figure>

Once we signup for the newsletter, we get another code:

<figure><img src="../../../.gitbook/assets/3 (118).png" alt=""><figcaption></figcaption></figure>

```
SIGNUP30
```

Now, all we have to do is add the "Lightweight l33t leather jacket" and apply the coupons in an alternating manner.

<figure><img src="../../../.gitbook/assets/5 (84).png" alt=""><figcaption></figcaption></figure>

This works because the server checks if the coupon is not applied right after itself but does not check if it is applied after another coupon.

<figure><img src="../../../.gitbook/assets/6 (68).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (54).png" alt=""><figcaption></figcaption></figure>

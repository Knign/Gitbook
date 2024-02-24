# Excessive trust in client-side controls

<figure><img src="../../../.gitbook/assets/1 (15).png" alt=""><figcaption></figcaption></figure>

We can click on the `My account` button and login using the following credentials:

| Username | Password |
| -------- | -------- |
| wiener   | peter    |

<figure><img src="../../../.gitbook/assets/2 (24).png" alt=""><figcaption></figcaption></figure>

We can now go back to the web store and click on the "Lightweight l33t leather jacket".

<figure><img src="../../../.gitbook/assets/3 (25).png" alt=""><figcaption></figcaption></figure>

Let's add the product to the cart.

<figure><img src="../../../.gitbook/assets/4 (22).png" alt=""><figcaption></figcaption></figure>

We can place the order but it won't go through because we don't have enough credits.

Since we are proxying the traffic Burp Suite, we can view this request through the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/5 (21).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Repeater` for further modifications. Once in the `Repeater`, we can set the `price` parameter to the following:

```
9
```

Let's send the request.

<figure><img src="../../../.gitbook/assets/6 (20).png" alt=""><figcaption></figcaption></figure>

If we check our cart through the browser, we can see that the price of the product has been set to the modified `price` parameter's value. The quantity has also been updated.

<figure><img src="../../../.gitbook/assets/7 (19).png" alt=""><figcaption></figcaption></figure>

Since the total price is less than our credits, we can now place the order.

<figure><img src="../../../.gitbook/assets/8 (9).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/9 (7).png" alt=""><figcaption></figcaption></figure>

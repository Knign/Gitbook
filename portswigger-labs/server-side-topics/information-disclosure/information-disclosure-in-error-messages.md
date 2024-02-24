# Information disclosure in error messages

<figure><img src="../../../.gitbook/assets/1 (146).png" alt=""><figcaption></figcaption></figure>

Let's click on the first product and view it.

<figure><img src="../../../.gitbook/assets/2 (138).png" alt=""><figcaption></figcaption></figure>

Since we are proxying the traffic through Burp Suite, we can view this request in the `Proxy > HTTP History`.

<figure><img src="../../../.gitbook/assets/3 (119).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` for further modification. Once in the `Repeater`, we have to set the `productId` parameter to a not-integer value as follows and send the request to the server:

```
"string"
```

<figure><img src="../../../.gitbook/assets/4 (100).png" alt=""><figcaption></figcaption></figure>

```
2 2.3.31
```

As we can see, the server discloses the Apache version in the response. We can not submit this as the answer.

<figure><img src="../../../.gitbook/assets/6 (69).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/7 (55).png" alt=""><figcaption></figcaption></figure>

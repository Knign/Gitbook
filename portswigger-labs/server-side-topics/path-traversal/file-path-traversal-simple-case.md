# File path traversal, simple case

<figure><img src="../../../.gitbook/assets/1 (133).png" alt=""><figcaption></figcaption></figure>

Let's access the image.

<figure><img src="../../../.gitbook/assets/2 (126).png" alt=""><figcaption></figcaption></figure>

We can now intercept this request in [Burp Suite](https://portswigger.net/burp) using the `Proxy`.

<figure><img src="../../../.gitbook/assets/3 (106).png" alt=""><figcaption></figcaption></figure>

As we can see the name of the image file is being passed into the `filename` parameter.

Now, we can forward the request to the `Repeater` to makes changes in it.

Let's change the `filename` parameter to the following and forward the request:

```
../../../etc/passwd
```

<figure><img src="../../../.gitbook/assets/4 (89).png" alt=""><figcaption></figcaption></figure>

We have successfully solved the challenge.

<figure><img src="../../../.gitbook/assets/5 (72).png" alt=""><figcaption></figcaption></figure>

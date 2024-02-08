# File path traversal, traversal sequences blocked with absolute path bypass

<figure><img src="../../../.gitbook/assets/1 (134).png" alt=""><figcaption></figcaption></figure>

Let's check out the image URI.

<figure><img src="../../../.gitbook/assets/2 (127).png" alt=""><figcaption></figcaption></figure>

We can intercept the request for this image in [Burp Suite](https://portswigger.net/burp) using the `Proxy`.

<figure><img src="../../../.gitbook/assets/3 (107).png" alt=""><figcaption></figcaption></figure>

Let's forward the request to the `Repeater` so the we can modify it.

Once in the `Repeater`, set the `filename` parameter to the following and forward the request:

```
../../../etc/passwd
```

<figure><img src="../../../.gitbook/assets/4 (90).png" alt=""><figcaption></figcaption></figure>

The server tells us that there is no such file. This is because the path in out URI is relative and is being stripped.

We can bypass this by using an absolute path as follows:

```
/etc/passwd
```

<figure><img src="../../../.gitbook/assets/5 (73).png" alt=""><figcaption></figcaption></figure>

We have successfully solved the lab.

<figure><img src="../../../.gitbook/assets/6 (59).png" alt=""><figcaption></figcaption></figure>

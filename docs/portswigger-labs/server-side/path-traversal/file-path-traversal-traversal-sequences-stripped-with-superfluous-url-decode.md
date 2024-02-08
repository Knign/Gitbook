# File path traversal, traversal sequences stripped with superfluous URL-decode

<figure><img src="../../../.gitbook/assets/1 (136).png" alt=""><figcaption></figcaption></figure>

Let's access the image.

<figure><img src="../../../.gitbook/assets/2 (129).png" alt=""><figcaption></figcaption></figure>

We can now intercept this request in [Burp Suite](https://portswigger.net/burp) using the `Proxy`.

<figure><img src="../../../.gitbook/assets/3 (110).png" alt=""><figcaption></figcaption></figure>

Now, we can forward the request to the `Repeater` to makes changes in it.

Let's change the `filename` parameter to the following and forward the request:

```
../../../etc/passwd
```

<figure><img src="../../../.gitbook/assets/4 (92).png" alt=""><figcaption></figcaption></figure>

The server tells us that the file does not exist. This is because the `../` characters are being stripped from our parameter.

| Original parameter  | Stripped parameter |
| ------------------- | ------------------ |
| ../../../etc/passwd | etc/passwd         |

We can bypass this by URI encoding the `../../../` character sequence. This way when the server tries to match the pattern, it won't find it because it has been encoded.

<figure><img src="../../../.gitbook/assets/5 (76).png" alt=""><figcaption></figcaption></figure>

Now we can set the `filename` parameter to the following:

```
%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66%25%32%65%25%32%65%25%32%66etc/passwd
```

<figure><img src="../../../.gitbook/assets/6 (61).png" alt=""><figcaption></figcaption></figure>

We have successfully solved the lab.

<figure><img src="../../../.gitbook/assets/7 (49).png" alt=""><figcaption></figcaption></figure>

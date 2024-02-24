# File path traversal, validation of file extension with null byte bypass

<figure><img src="../../../.gitbook/assets/1 (137).png" alt=""><figcaption></figcaption></figure>

Let's access the image through the browser.

<figure><img src="../../../.gitbook/assets/2 (130).png" alt=""><figcaption></figcaption></figure>

We can now intercept this request in Burp Suite using the `Proxy`.

<figure><img src="../../../.gitbook/assets/3 (111).png" alt=""><figcaption></figcaption></figure>

Now, we can forward the request to the `Repeater` to makes changes in it.

Let's change the `filename` parameter to the following and forward the request:

```
../../../etc/passwd
```

<figure><img src="../../../.gitbook/assets/4 (93).png" alt=""><figcaption></figcaption></figure>

The server expects a `.png` file extension. We can use `%00` characters before the extension so that our string gets terminated before the extension

```
../../../etc/passwd%00.png
```

<figure><img src="../../../.gitbook/assets/5 (77).png" alt=""><figcaption></figcaption></figure>

We have successfully solved the lab.

<figure><img src="../../../.gitbook/assets/6 (63).png" alt=""><figcaption></figcaption></figure>

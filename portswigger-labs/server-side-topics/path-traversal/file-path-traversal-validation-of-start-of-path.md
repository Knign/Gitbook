# File path traversal, validation of start of path

<figure><img src="../../../.gitbook/assets/1 (18).png" alt=""><figcaption></figcaption></figure>

Let's access the image through the browser.

<figure><img src="../../../.gitbook/assets/2 (26).png" alt=""><figcaption></figcaption></figure>

We can now intercept this request in Burp Suite using the `Proxy`.

<figure><img src="../../../.gitbook/assets/3 (28).png" alt=""><figcaption></figcaption></figure>

Now, we can forward the request to the `Repeater` to makes changes in it.

Let's change the `filename` parameter to the following and forward the request:

```
/etc/passwd
```

<figure><img src="../../../.gitbook/assets/4 (24).png" alt=""><figcaption></figcaption></figure>

The server requires the user-supplied filename to start with `/var/www/images`.

```
/var/www/images/../../../etc/passwd
```

<figure><img src="../../../.gitbook/assets/5 (24).png" alt=""><figcaption></figcaption></figure>

We have successfully solved the lab.

<figure><img src="../../../.gitbook/assets/6 (62).png" alt=""><figcaption></figcaption></figure>

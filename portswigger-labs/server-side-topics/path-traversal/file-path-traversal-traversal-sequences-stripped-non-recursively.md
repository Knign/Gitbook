# File path traversal, traversal sequences stripped non-recursively

<figure><img src="../../../.gitbook/assets/1 (135).png" alt=""><figcaption></figcaption></figure>

Let's access the image through the browser.

<figure><img src="../../../.gitbook/assets/2 (128).png" alt=""><figcaption></figcaption></figure>

We can intercept this request in [Burp Suite](https://portswigger.net/burp) using the `Proxy`.

<figure><img src="../../../.gitbook/assets/3 (109).png" alt=""><figcaption></figcaption></figure>

Now, we can sent this intercepted request to the `Repeater` to modify it.

Once in the `Repeater`, we can set the `filename` parameter to the following:

```
../../../etc/passwd
```

<figure><img src="../../../.gitbook/assets/4 (91).png" alt=""><figcaption></figcaption></figure>

The server tells us that the file does not exist. This is because the `../` characters are being stripped from our parameter.

| Original            | Stripped   |
| ------------------- | ---------- |
| ../../../etc/passwd | etc/passwd |

The problem is, the server does not strip the parameters recursively,&#x20;

We can exploit it by setting the `filename` parameter to the following:

```
....//....//....//etc/passwd
```

Now, when the `../` characters are stripped it still leaves a set of `../` characters.

| Original                     | Stripped            |
| ---------------------------- | ------------------- |
| ....//....//....//etc/passwd | ../../../etc/passwd |

<figure><img src="../../../.gitbook/assets/5 (75).png" alt=""><figcaption></figcaption></figure>

We have successfully solved the lab.

<figure><img src="../../../.gitbook/assets/6 (60).png" alt=""><figcaption></figcaption></figure>

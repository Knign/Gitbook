# Javascript - Obfuscation 1

<figure><img src="../../.gitbook/assets/1 (67).png" alt=""><figcaption></figcaption></figure>

Let's check the source code with `CTRL + U`.

<figure><img src="../../.gitbook/assets/2 (65).png" alt=""><figcaption></figcaption></figure>

We can see that the password is Hex-encoded.

We can decode it using the `decodeURI` function.

<figure><img src="../../.gitbook/assets/3 (59).png" alt=""><figcaption></figcaption></figure>

```javascript
> decodeURI("%63%70%61%73%62%69%65%6e%64%75%72%70%61%73%73%77%6f%72%64")
<- 'cpasbiendurpassword'
```

Let's enter the decoded password.

<figure><img src="../../.gitbook/assets/4 (48).png" alt=""><figcaption></figcaption></figure>

## Password

```
cpasbiendurpassword
```

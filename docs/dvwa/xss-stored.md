# XSS (Stored)

> #### Objective
>
> Redirect everyone to a web page of your choosing.

##

## Security Level: Low

> Low level will not check the requested input, before including it to be used in the output text. Spoiler: Either name or message field: alert("XSS");.

<figure><img src="../.gitbook/assets/1 (41).png" alt=""><figcaption></figcaption></figure>

* We can provide any random string as the input.

<figure><img src="../.gitbook/assets/2 (38).png" alt=""><figcaption></figcaption></figure>

* As we can see, our input has been stored on the server.
* Let's provide the following input in order to obtain the cookie.

```
<script>alert()</script>
```

<figure><img src="../.gitbook/assets/3 (90).png" alt=""><figcaption></figcaption></figure>

* Anytime a user visits this page and their browser renders our message, they will get this alert.

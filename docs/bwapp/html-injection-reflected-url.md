# HTML Injection - Reflected (URL)

## Security level: low

<figure><img src="../.gitbook/assets/1 (105).png" alt=""><figcaption></figcaption></figure>

* The application prints our current URL on the page.
* Let's turn on the intercept in Burpsuite and reload the page.

<figure><img src="../.gitbook/assets/2 (99).png" alt=""><figcaption></figcaption></figure>

* We can change the `Host:` field to any value we want.

```
Host: getHacked
```

* Let's turn off the intercept so that the request reaches to the server.

<figure><img src="../.gitbook/assets/3 (86).png" alt=""><figcaption></figcaption></figure>

* We have successfully performed HTML injection.

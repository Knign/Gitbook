# HTTP - Verb tampering

> Bypass the security establishment.

<figure><img src="../../.gitbook/assets/1 (103).png" alt=""><figcaption></figcaption></figure>

On visiting the site, we are prompted to enter the user and password.

Let's intercept this request in Burpsuite.

<figure><img src="../../.gitbook/assets/2 (98).png" alt=""><figcaption></figcaption></figure>

We can now forward the request to the `Intruder`.&#x20;

<figure><img src="../../.gitbook/assets/3 (85).png" alt=""><figcaption></figcaption></figure>

After we have selected the request method, we can set the payload.

For the payload, we are using all the request methods.

<figure><img src="../../.gitbook/assets/4 (67).png" alt=""><figcaption></figcaption></figure>

Let's send this payload and check the response.

<figure><img src="../../.gitbook/assets/5 (57).png" alt=""><figcaption></figcaption></figure>

## Flag

```
a23e$dme96d3saez$$prap
```

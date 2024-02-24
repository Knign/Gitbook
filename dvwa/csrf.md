# CSRF

> #### Objective
>
> Your task is to make the current user change their own password, without them knowing about their actions, using a CSRF attack.

##

## Security Level: Low

> There are no measures in place to protect against this attack. This means a link can be crafted to achieve a certain action (in this case, change the current users password). Then with some basic social engineering, have the target click the link (or just visit a certain page), to trigger the action. Spoiler: ?password\_new=password\&password\_conf=password\&Change=Change.&#x20;

<figure><img src="../.gitbook/assets/1 (106).png" alt=""><figcaption></figcaption></figure>

* Let's click on the `Test Credentials` button and enter `password` as the password.

<figure><img src="../.gitbook/assets/2 (101).png" alt=""><figcaption></figcaption></figure>

* We can now set the password to any other value let's say `password123` and intercept the request using Burpsuite.

<figure><img src="../.gitbook/assets/4 (68).png" alt=""><figcaption></figcaption></figure>

* As we can see, the passwords are being used in the URI.
* We can use the following URL and set the password back to `password`.

```
http://10.0.4.5/DVWA/vulnerabilities/csrf/?password_new=password&password_conf=password&Change=Change
```

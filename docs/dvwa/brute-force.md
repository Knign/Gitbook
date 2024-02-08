# Brute Force

> #### Objective
>
> Your goal is to get the administrator’s password by brute forcing. Bonus points for getting the other four user passwords!

##

## Security Level: Low

<figure><img src="../.gitbook/assets/1 (45).png" alt=""><figcaption></figcaption></figure>

* The application provides us with two input fields in order to enter the username and the password.
* Let's enter `admin` as both.

<figure><img src="../.gitbook/assets/2 (42).png" alt=""><figcaption></figcaption></figure>

* Let's intercept the request in Burpsuite.

<figure><img src="../.gitbook/assets/3 (39).png" alt=""><figcaption></figcaption></figure>

* We can now forward this request to the `Intruder` to automate the attack.

<figure><img src="../.gitbook/assets/4 (36).png" alt=""><figcaption></figcaption></figure>

* After adding a field to the password, we can move on to setting up the substitution payload.&#x20;

<figure><img src="../.gitbook/assets/5 (36).png" alt=""><figcaption></figcaption></figure>

* For the payload type we want a simple list, more specifically the `darkweb2017-top100.txt` passwords lists from the `seclists` collection.
* Before we start the attack there is something important that we have to do.
* In the `Options` tab, we can set the string to grep for. We can set it to the following:

```
Username and/or password incorrect.
```

<figure><img src="../.gitbook/assets/6 (36).png" alt=""><figcaption></figcaption></figure>

* Let's start the attack.

<figure><img src="../.gitbook/assets/7 (32).png" alt=""><figcaption></figcaption></figure>

* We can immediately see that the response for `password` did not include the string.
* Let's take a closer look at the response.

<figure><img src="../.gitbook/assets/8 (26).png" alt=""><figcaption></figcaption></figure>

* We can see that it greets us with a welcome message. This means that the password is `password`.

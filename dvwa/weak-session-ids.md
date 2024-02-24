# Weak Session IDs

> #### Objective
>
> This module uses four different ways to set the dvwaSession cookie value, the objective of each level is to work out how the ID is generated and then infer the IDs of other system users.

##

## Security Level: Low

> The cookie value should be very obviously predictable.&#x20;

<figure><img src="../.gitbook/assets/1 (107).png" alt=""><figcaption></figcaption></figure>

* Let's inspect the page and check for the cookies.&#x20;

<figure><img src="../.gitbook/assets/2 (102).png" alt=""><figcaption></figcaption></figure>

* As we can see, the `dvwaSession` cookie is set to 1. Let's click on the `Generate` button and check what happens.

<figure><img src="../.gitbook/assets/3 (88).png" alt=""><figcaption></figcaption></figure>

* The `dvwaSession` cookie is now set to 1. Now we know that the application increments the cookie every time the user clicks on the `Generate` button.
* We could also check the provided source code to be sure.

<figure><img src="../.gitbook/assets/4 (69).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: Medium

> The value looks a little more random than on low but if you collect a few you should start to see a pattern.

* In this level the value of the `dvwaSession` cookie increments by 1 the first we click the button and then by 2.
* This process is repeated as many times as the user clicks the button.

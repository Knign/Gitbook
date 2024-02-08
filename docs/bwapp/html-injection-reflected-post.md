# HTML Injection - Reflected (POST)

## Security level: low

<figure><img src="../.gitbook/assets/1 (48).png" alt=""><figcaption></figcaption></figure>

* We are provided with two input fields to input the first and last name.
* Let's provide the input and intercept the request in Burpsuite.

<figure><img src="../.gitbook/assets/2 (46).png" alt=""><figcaption></figcaption></figure>

* We can see that the request method is POST.
* Let's input the following HTML tag:

```
First name: 
<h1>john</h1>

Last name: 
<h2>doe</h2>
```

<figure><img src="../.gitbook/assets/3 (42).png" alt=""><figcaption></figcaption></figure>

##

## Security level: medium

* Let's intercept the request using Burpsuite.

<figure><img src="../.gitbook/assets/4 (38).png" alt=""><figcaption></figcaption></figure>

* As we can see, our input HTML characters have been URL encoded.
* Let's encode the entire input including the name to check if that evades the security filter.

<figure><img src="../.gitbook/assets/5 (38).png" alt=""><figcaption></figcaption></figure>

```
firstname:
%3c%68%31%3e%6a%6f%68%6e%3c%2f%68%31%3e

lastname:
%3c%68%32%3e%64%6f%65%3c%2f%68%32%3e
```

<figure><img src="../.gitbook/assets/6 (39).png" alt=""><figcaption></figcaption></figure>

* We have successfully exploited the HTML injection vulnerability.

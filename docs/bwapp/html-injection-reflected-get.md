# HTML Injection - Reflected (GET)

## Security level: low

<figure><img src="../.gitbook/assets/1 (51).png" alt=""><figcaption></figcaption></figure>

* We are provided with two input fields to enter the first and last name.
* Let's give it some random name and see what happens.

<figure><img src="../.gitbook/assets/2 (48).png" alt=""><figcaption></figcaption></figure>

* Looks like our input is reflected back on the screen.

### HTML injection

* HTML injection is a type of injection when the user is able to enter arbitrary HTML code in a web page. This allows us to modify the contents of the page.
* Let's input the following HTML tag:

```
First name: 
<h1>john</h1>

Last name: 
<h2>doe</h2>
```

<figure><img src="../.gitbook/assets/3 (45).png" alt=""><figcaption></figcaption></figure>

##

## Security level: medium

* Let's try inserting the same input as before.

```
First name: 
<h1>john</h1>

Last name: 
<h2>doe</h2>
```

<figure><img src="../.gitbook/assets/4 (39).png" alt=""><figcaption></figcaption></figure>

* This time the input is not treated as HTML code.
* We can intercept the request in Burpsuite to check how out input is being treated.

<figure><img src="../.gitbook/assets/5 (39).png" alt=""><figcaption></figcaption></figure>

* As we can see the input is URL encoded. We can also check this out in the `Decoder`.

<figure><img src="../.gitbook/assets/6 (40).png" alt=""><figcaption></figcaption></figure>

* We can bypass the security filter using double URL encoding as suggested in [this](https://owasp.org/www-community/Double\_Encoding) OWASP document.

### Double URL encoding

<figure><img src="../.gitbook/assets/7 (33).png" alt=""><figcaption></figcaption></figure>

```
%25%33%63%25%36%38%25%33%31%25%33%65%25%36%61%25%36%66%25%36%38%25%36%65%25%33%63%25%32%66%25%36%38%25%33%31%25%33%65
```

* Let's forward the request to the `Repeater` so that we can make modifications.
* We can now provide the double encoded string as the input.&#x20;

<figure><img src="../.gitbook/assets/8 (24).png" alt=""><figcaption></figcaption></figure>

* As we can see the name is now treated as an `h1` element. This means we have successfully performed URL injection.

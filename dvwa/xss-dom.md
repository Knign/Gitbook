# XSS (DOM)

> #### Objective
>
> Run your own JavaScript in another user's browser, use this to steal the cookie of a logged in user.

##

## Security Level: Low

> Low level will not check the requested input, before including it to be used in the output text. Spoiler: /vulnerabilities/xss\_d/?default=Englishalert(1).

* Let's select the first option i.e. `English` and click `Submit`.

<figure><img src="../.gitbook/assets/1 (108).png" alt=""><figcaption></figcaption></figure>

* If we look at the URL, we can see that our input has been set as a URL parameter.
* DOM-based XSS vulnerabilities usually arise when JavaScript takes data from an attacker-controllable source, such as the URL, and passes it to a sink that supports dynamic code execution.
* Let's change the URL to the following:

```
10.0.4.5/DVWA/vulnerabilities/xss_d/?default=<script>alert();</script>
```

<figure><img src="../.gitbook/assets/2 (103).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: Medium

> The developer has tried to add a simple pattern matching to remove any references to "\<script" to disable any JavaScript. Find a way to run JavaScript without using the script tags. Spoiler: You must first break out of the select block then you can add an image with an onerror event:\
> /vulnerabilities/xss\_d/?default=English>/option>.

* Let's check the source code.&#x20;

<figure><img src="../.gitbook/assets/3 (89).png" alt=""><figcaption></figcaption></figure>

* So our input is being stripped of `<script` tags.
* Let's inspect the code in the web page as well.&#x20;

<figure><img src="../.gitbook/assets/4 (70).png" alt=""><figcaption></figcaption></figure>

* We can see that we first need to escape the `<select>` tag that we are in.
* Once we have done that we can use the `img onerror` attribute to trigger an alert.

```
10.0.4.5/DVWA/vulnerabilities/xss_d/?default=</select><img src=1 onerror=alert(document.cookie)>
```

<figure><img src="../.gitbook/assets/5 (58).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: High

> The developer is now white listing only the allowed languages, you must find a way to run your code without it going to the server. Spoiler: The fragment section of a URL (anything after the # symbol) does not get sent to the server and so cannot be blocked. The bad JavaScript being used to render the page reads the content from it when creating the page.\
> /vulnerabilities/xss\_d/?default=English#alert(1).

* Let's check the source code first.

<figure><img src="../.gitbook/assets/6 (48).png" alt=""><figcaption></figcaption></figure>

* In this case we can use the `#` character so that our URI is fragmented and it satisfies the checks.

```
10.0.4.5/DVWA/vulnerabilities/xss_d/#?default=<script>alert(document.cookie);</script>
```

<figure><img src="../.gitbook/assets/7 (37).png" alt=""><figcaption></figcaption></figure>

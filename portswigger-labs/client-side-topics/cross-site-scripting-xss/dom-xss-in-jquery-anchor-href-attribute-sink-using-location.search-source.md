---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-jquery-href-attribute-sink
---

# DOM XSS in jQuery anchor href attribute sink using location.search source

<figure><img src="../../../.gitbook/assets/1 (168).png" alt=""><figcaption></figcaption></figure>

Let's click on the `Submit Feedback` button.

On the `Submit Feedback` page, we can open the developer tools and inspect the `Back` link.

<figure><img src="../../../.gitbook/assets/2 (149).png" alt=""><figcaption></figcaption></figure>

We can see that it is an `<a>` tag with the `backLink` ID and `href="/"`.&#x20;

Right below it, we can see the script which is responsible for setting it's `href` attribute.

```js
$(function() {
    $('#backLink').attr("href", (new URLSearchParams(window.location.search)).get('returnPath'));
});
```

* `$(function() {...})`: This is a shorthand for `$(document).ready(function() {...})`, which ensures that the code inside the function is executed when the DOM is fully loaded.
* `$('#backLink')`: Selects the HTML element with the ID 'backLink'.
* `.attr("href", ...)`: Sets the 'href' attribute of the selected element.
* `(new URLSearchParams(window.location.search)).get('returnPath')`: Retrieves the value of the 'returnPath' parameter from the URL using the `URLSearchParams` API.

Now that we know how the script works, we can set the `returnPath` parameter in the URI to the following:

```
javascript:alert(document.cookie)
```

<figure><img src="../../../.gitbook/assets/3 (131).png" alt=""><figcaption></figcaption></figure>

Let's inspect the `Back` link to see if our payload has been inserted.

<figure><img src="../../../.gitbook/assets/4 (112).png" alt=""><figcaption></figcaption></figure>

Now if we click on the `Back` link, the Javascript that has been inserted in the `href` attribute will be executed.

<figure><img src="../../../.gitbook/assets/5 (93).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/6 (79).png" alt=""><figcaption></figcaption></figure>

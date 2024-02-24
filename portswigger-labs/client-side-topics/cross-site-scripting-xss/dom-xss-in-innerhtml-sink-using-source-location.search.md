---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-innerhtml-sink
---

# DOM XSS in innerHTML sink using source location.search

<figure><img src="../../../.gitbook/assets/1 (167).png" alt=""><figcaption></figcaption></figure>

Let's insert the following payload in the search field:

```
test_payload
```

We can now open the developer tools and search our payload.

<figure><img src="../../../.gitbook/assets/2 (148).png" alt=""><figcaption></figcaption></figure>

We can see that our payload has been inserted in the `<span>` tag more specifically, it has been appended to the source of the image.

Right below that we can see a `<script>` tag which includes the script responsible for the DOM manipulation:

```js
function doSearchQuery(query) {
    document.getElementById('searchMessage').innerHTML = query;
}
var query = (new URLSearchParams(window.location.search)).get('search');
if (query) {
    doSearchQuery(query);
}
```

* The `doSearchQuery` function takes a `query` parameter and sets the inner HTML of an element with the ID `searchMessage` to the query value.
* The `query` variable is assigned the value of the 'search' parameter from the URL using `URLSearchParams`.
* If the 'search' parameter exists in the URL, the `doSearchQuery` function is called with the obtained query.

Now that we know how the DOM manipulation works, we can insert our final payload into the application which will generate an alert.

```
<img src=1 onerror=alert("1")>
```

<figure><img src="../../../.gitbook/assets/3 (130).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/4 (110).png" alt=""><figcaption></figcaption></figure>

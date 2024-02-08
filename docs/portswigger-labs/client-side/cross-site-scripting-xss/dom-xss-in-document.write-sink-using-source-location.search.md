---
description: >-
  https://portswigger.net/web-security/cross-site-scripting/dom-based/lab-document-write-sink
---

# DOM XSS in document.write sink using source location.search

<figure><img src="../../../.gitbook/assets/1 (2).png" alt=""><figcaption></figcaption></figure>

Let's insert the following payload in the search field:

```
test_payload
```

We can now open the developer tools and search our payload.

<figure><img src="../../../.gitbook/assets/2 (3).png" alt=""><figcaption></figcaption></figure>

We can see that our payload has been inserted in the `<img>` tag more specifically, it has been appended to the source of the image.

Right above that we can see a `<script>` tag which includes the script responsible for the DOM manipulation:

```js
function trackSearch(query) {
    document.write('<img src="/resources/images/tracker.gif?searchTerms=' + query + '">');
}
var query = (new URLSearchParams(window.location.search)).get('search');
if (query) {
    trackSearch(query);
}
```

* The `trackSearch()` function takes a `query` parameter and writes an image tag to the document, where the `src` attribute includes the search terms.
* The `query` variable is then assigned the value of the 'search' parameter from the URL using `URLSearchParams`.
* If the 'search' parameter exists in the URL, the `trackSearch()` function is called with the obtained query.

Now that we know how the DOM manipulation works, we can insert our final payload into the application which will generate an alert.

```
"><svg onload=alert(1)>
```

<figure><img src="../../../.gitbook/assets/3 (4).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/5 (2).png" alt=""><figcaption></figcaption></figure>

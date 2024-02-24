# Change your browser

<figure><img src="../../.gitbook/assets/1 (94).png" alt=""><figcaption></figcaption></figure>

* The challenge expects our browser to be `W3Challs_browser`.
* We can begin by proxying the request through Burpsuite.&#x20;

<figure><img src="../../.gitbook/assets/2 (52).png" alt=""><figcaption></figcaption></figure>

* Let's send this request to the `Repeater`.&#x20;

<figure><img src="../../.gitbook/assets/3 (48).png" alt=""><figcaption></figcaption></figure>

### User-Agent

```
User-Agent: Mozilla/5.0 (<system-information>) <platform> (<platform-details>) <extensions>
```

* The `User-Agent` holds information about the browser the client is using.
* We can replace the header to `W3Challs_browser`.

### HTTP Request

```
GET / HTTP/1.1
Host: change-browser.hax.w3challs.com
User-Agent: W3Challs_browser
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
DNT: 1
Connection: close
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
```

* Next we have to send this modified request to the server.

<figure><img src="../../.gitbook/assets/4 (41).png" alt=""><figcaption></figcaption></figure>

### Flag

```
W3C{now_that_we_have_the_right_browser_lets_get_the_party_started}
```

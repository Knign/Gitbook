# HTTP - Headers

<figure><img src="../../.gitbook/assets/1 (95).png" alt=""><figcaption></figcaption></figure>

* Maybe the clue lie in the response headers.
* In order to check the response headers we have to intercept the request using Burpsuite.&#x20;

<figure><img src="../../.gitbook/assets/2 (91).png" alt=""><figcaption></figcaption></figure>

* Let's forward the request to the `Repeater`.

<figure><img src="../../.gitbook/assets/3 (78).png" alt=""><figcaption></figcaption></figure>

* The response has a header called `Header-RootMe-Admin`. We can include this header in our next request.

### HTTP Request

```
GET /web-serveur/ch5/ HTTP/1.1
Host: challenge01.root-me.org
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/118.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Header-RootMe-Admin: none
DNT: 1
Connection: close
Cookie: _ga_SRYSKX09J7=GS1.1.1697389021.11.1.1697389201.0.0.0; _ga=GA1.1.1863804672.1697290591
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
```

* Finally, we have to send this request to the server.

<figure><img src="../../.gitbook/assets/4 (62).png" alt=""><figcaption></figcaption></figure>

### Flag

```
HeadersMayBeUseful
```

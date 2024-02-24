# HTTP - User-agent

<figure><img src="../../.gitbook/assets/1 (100).png" alt=""><figcaption></figcaption></figure>

Let's intercept the request using Burpsuite so that we can modify it.

<figure><img src="../../.gitbook/assets/2 (95).png" alt=""><figcaption></figcaption></figure>

We can now send the request to `Repeater`.&#x20;

<figure><img src="../../.gitbook/assets/3 (82).png" alt=""><figcaption></figcaption></figure>

## User-Agent

The **User-Agent** request header is a characteristic string that lets servers and network peers identify the application, browser used to make the request.

We have to modify it to `admin`.

## HTTP Request

```
GET /web-serveur/ch2/ HTTP/1.1
Host: challenge01.root-me.org
User-Agent: admin
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate, br
DNT: 1
Connection: close
Cookie: _ga_SRYSKX09J7=GS1.1.1697381490.9.1.1697381491.0.0.0; _ga=GA1.1.1863804672.1697290591
Upgrade-Insecure-Requests: 1
Sec-GPC: 1
```

Finally, we have to send the request to the server.

<figure><img src="../../.gitbook/assets/4 (64).png" alt=""><figcaption></figcaption></figure>

## Flag

```
rr$Li9%L34qd1AAe27
```

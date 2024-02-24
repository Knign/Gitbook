# Blind OS command injection with time delays

<figure><img src="../../../.gitbook/assets/1 (17).png" alt=""><figcaption></figcaption></figure>

Let's submit the feedback for one of these products.

<figure><img src="../../../.gitbook/assets/3 (27).png" alt=""><figcaption></figcaption></figure>

We can now proxy the traffic through Burp Suite.

<figure><img src="../../../.gitbook/assets/4 (23).png" alt=""><figcaption></figcaption></figure>

Let's forward this request to the `Repeater` so that we can modify it. Once in the `Repeater` we can set the `email` parameter to the following and send the request:

```
x%40gmail.com||ping+-c+10+127.0.0.1||
```

<figure><img src="../../../.gitbook/assets/5 (23).png" alt=""><figcaption></figcaption></figure>

The response takes 10 seconds to return. We have solved the lab.

<figure><img src="../../../.gitbook/assets/6 (22).png" alt=""><figcaption></figcaption></figure>

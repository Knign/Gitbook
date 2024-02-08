# OS command injection, simple case

<figure><img src="../../../.gitbook/assets/1 (138).png" alt=""><figcaption></figcaption></figure>

Let's check the first product's stock.

<figure><img src="../../../.gitbook/assets/2 (131).png" alt=""><figcaption></figcaption></figure>

We can intercept this request using the Burp Suite `Proxy` and forward it to the `Repeater` to modify it.

<figure><img src="../../../.gitbook/assets/3 (112).png" alt=""><figcaption></figcaption></figure>

Now let's set the `storeID` parameter to the following and send the request:

```
1|whoami
```

<figure><img src="../../../.gitbook/assets/4 (94).png" alt=""><figcaption></figcaption></figure>

We have solved the lab.

<figure><img src="../../../.gitbook/assets/5 (78).png" alt=""><figcaption></figcaption></figure>

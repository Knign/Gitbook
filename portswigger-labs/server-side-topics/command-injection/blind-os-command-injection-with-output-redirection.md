# Blind OS command injection with output redirection

<figure><img src="../../../.gitbook/assets/1 (139).png" alt=""><figcaption></figcaption></figure>

Let's submit some feedback.

<figure><img src="../../../.gitbook/assets/2 (132).png" alt=""><figcaption></figcaption></figure>

We can proxy this request through Burp Suite and check the `Proxy > HTTP History` tab.

<figure><img src="../../../.gitbook/assets/3 (113).png" alt=""><figcaption></figcaption></figure>

Let's forward it to the `Repeater` for modification. Once in the `Repeater` set the `email` parameter to the following and send the request:

```
x%40gmail.com||whoami>/var/www/images/output.txt||
```

<figure><img src="../../../.gitbook/assets/4 (95).png" alt=""><figcaption></figcaption></figure>

The out put of our `whoami` command is now saved in the `/var/www/images/output.txt` file. Now let's view one of the images through our browser.

<figure><img src="../../../.gitbook/assets/5 (79).png" alt=""><figcaption></figcaption></figure>

Let's go to the `Proxy > HTTP History` tab in Burp Suite and view this request.

<figure><img src="../../../.gitbook/assets/6 (64).png" alt=""><figcaption></figcaption></figure>

After forwarding this request to the `Repeater`, we can set the `filename` parameter to the following:

```
output.txt
```

<figure><img src="../../../.gitbook/assets/7 (50).png" alt=""><figcaption></figcaption></figure>

There's the output of our command. We have solved the lab.

<figure><img src="../../../.gitbook/assets/8 (38).png" alt=""><figcaption></figcaption></figure>

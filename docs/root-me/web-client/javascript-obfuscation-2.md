# Javascript - Obfuscation 2

<figure><img src="../../.gitbook/assets/1 (79).png" alt=""><figcaption></figcaption></figure>

* The page is empty. Let's check the source code.

<figure><img src="../../.gitbook/assets/2 (79).png" alt=""><figcaption></figcaption></figure>

* Looks like password has been encoded multiple times. We can use the `decodeURI` function to decode it.

<figure><img src="../../.gitbook/assets/3 (57).png" alt=""><figcaption></figcaption></figure>

```js
> decodeURI("unescape%28%22String.fromCharCode%2528104%252C68%252C117%252C102%252C106%252C100%252C107%252C105%252C49%252C53%252C54%2529%22%29")
<- 'unescape("String.fromCharCode%28104%2C68%2C117%2C102%2C106%2C100%2C107%2C105%2C49%2C53%2C54%29")'
> decodeURIComponent("String.fromCharCode%28104%2C68%2C117%2C102%2C106%2C100%2C107%2C105%2C49%2C53%2C54%29")
<- 'String.fromCharCode(104,68,117,102,106,100,107,105,49,53,54)'
> String.fromCharCode(104,68,117,102,106,100,107,105,49,53,54)
<- 'hDufjdki156'
```

### Password

```
hDufjdki156
```

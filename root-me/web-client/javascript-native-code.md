# Javascript - Native code

<figure><img src="../../.gitbook/assets/1 (80).png" alt=""><figcaption></figcaption></figure>

The website prompts us to enter a password.

Let's check the source code.

<figure><img src="../../.gitbook/assets/2 (80).png" alt=""><figcaption></figcaption></figure>

If we replace the last pair of brackets, to `toString()`, we can see the deobfuscated Javascript.

<figure><img src="../../.gitbook/assets/3 (69).png" alt=""><figcaption></figcaption></figure>

```js
function anonymous() 
{
	a=prompt('Entrez le mot de passe');
	if(a=='toto123lol'){
		alert('bravo');
	}else{
		alert('fail...');
	}
}
```

### Password

```
toto123lol
```

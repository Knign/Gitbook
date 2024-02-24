# Postbook

## Flag 0

> Hint: The person with username “user” has a very easy password…

What could an “easy password” mean?

A quick search on Google tells us that the most common passwords are:

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*19qY-Vyu3rXT7v2dvx_tFg.png" alt=""><figcaption></figcaption></figure>

Lets try out typing “Password”.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*xXy4hLxlG5xMGRWbV3Ev_w.png" alt=""><figcaption></figcaption></figure>

There we have it! Our first flag.



## Flag 1

> _Hint: Try viewing your own post and then see if you can change the ID_

We can see that the post id is “3”.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*cN6_xgIeXZIg93-CzLRzwg.png" alt=""><figcaption></figcaption></figure>

Lets flip it to “2”.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*3cfNIfxD9uvi-Tp3JYQkdQ.png" alt=""><figcaption></figcaption></figure>

There’s our flag.



## Flag 2

> Hint: You should definitely use “Inspect Element” on the form when creating a new post

If we go in the Inspect Element and look at the form we can see that the value for the “user\_id” is 2

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*CZvqN7h4FwiQ7O9N7yK_qg.png" alt=""><figcaption></figcaption></figure>

* We can try switching this value to 1.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*pCbiMFroFX4zepxokNp5HQ.png" alt=""><figcaption></figcaption></figure>

A wild flag appears!



## Flag 3

> _Hint: 189 \* 5_

Let’s try this number as the post id.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*5SegG89Hk_mrfTZwxK4csA.png" alt=""><figcaption></figcaption></figure>

And we have our flag.



## Flag4

> _Hint: You can edit your own posts, what about someone else’s?_

If go to the edit option of our post, we can see that the post id is 3.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*iQF7-FSYCETmfrjqiNtfPg.png" alt=""><figcaption></figcaption></figure>

By changing the post id to 1, we can access the admin’s post.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*SwALngxMmZmFL1p0zJ30dA.png" alt=""><figcaption></figcaption></figure>

After editing and saving the post we are presented with the flag.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*zGdlTyUyFMaSjRqlp0njmw.png" alt=""><figcaption></figcaption></figure>



## Flag 5

> _Hint: The cookie allows you to stay signed in. Can you figure out how they work so you can sign in to user with ID 1?_

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*jQf4K0BCxucu-XwzxsXpAQ.png" alt=""><figcaption></figcaption></figure>

If we go to Inspect Element > Application > Cookies, we can see that the id is stored as a MD5 hash value. On decrypting, we come to find out that the value is “2”.

We already know that the admin id is “1”. The next step is to convert 1 to a MD5 hash and enter the hash in the id field.

On hitting refresh, the flag is triggered.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*rQBWTdPbjJ3aoXXVAQE4DQ.png" alt=""><figcaption></figcaption></figure>



## Flag 6

> _Hint: Deleting a post seems to take an ID that is not a number. Can you figure out what it is?_

If we inspect the delete button, we can see that it has an id in the form of MD5 hash as well.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*h1jNfo-gX00Bep2j3gXyug.png" alt=""><figcaption></figcaption></figure>

Now, we simply have to replace this value with the hash of 1 and then press the delete button.

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*aPkmNZolYT44svXSo-CSkQ.png" alt=""><figcaption></figcaption></figure>

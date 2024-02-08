# XSS (Reflected)

> #### Objective
>
> One way or another, steal the cookie of a logged in user.

##

## Security Level: Low

> Low level will not check the requested input, before including it to be used in the output text. Spoiler: ?name=alert("XSS");.

<figure><img src="../.gitbook/assets/1 (40).png" alt=""><figcaption></figcaption></figure>

* Let's prove `john` as the input.&#x20;

<figure><img src="../.gitbook/assets/2 (37).png" alt=""><figcaption></figcaption></figure>

* We can see that our input is being reflected back to us.
* Let's provide the following input:

```
<script>alert(document.cookie)</script>
```

<figure><img src="../.gitbook/assets/3 (35).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: Medium

> The developer has tried to add a simple pattern matching to remove any references to "", to disable any JavaScript. Spoiler: Its cAse sENSiTiVE.

* Let's check out the source code.

<figure><img src="../.gitbook/assets/4 (33).png" alt=""><figcaption></figcaption></figure>

* The `<script>` tag is being replaced with empty space using the `str_replace` function.
* The problem with this function is that it is case sensitive i.e. it will not replace a `<SCRIPT>` tag.
* This allows us to craft our payload as follows:

```
<SCRIPT>alert(document.cookie)</SCRIPT>
```

<figure><img src="../.gitbook/assets/5 (33).png" alt=""><figcaption></figcaption></figure>

##

## Security Level: High

> The developer now believes they can disable all JavaScript by removing the pattern "\<s_c_r_i_p\*t". Spoiler: HTML events.

* In this level the `<script` pattern itself is removed.
* Let's check the source code to see how this has been implemented.&#x20;

<figure><img src="../.gitbook/assets/6 (33).png" alt=""><figcaption></figcaption></figure>

* The developer has used the `preg_replace` function.
* However, we can still use HTML events in order to trigger the alert.
* For our payload we can use the `<img onerror>` attribute as follows:

```
<img src=1 onerror=alert(document.cookie)>
```

<figure><img src="../.gitbook/assets/7 (29).png" alt=""><figcaption></figcaption></figure>

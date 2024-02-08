# Phishing Email

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}

##

## Question 1

> What is the return path of the email?

* Let's first open the email using the [Thunderbird](https://www.thunderbird.net/en-US/) client.

<figure><img src="../../../.gitbook/assets/1 (54).png" alt=""><figcaption></figcaption></figure>

* If we go to `More > View Source`, we can see the HTML source of the email.

<figure><img src="../../../.gitbook/assets/2 (53).png" alt=""><figcaption></figcaption></figure>

* There is also a `Return-Path` field which contains the answer.

### Answer

```
bounce@rjttznyzjjzydnillquh.designclub.uk.com
```

##

## Question 2

> What is the domain name of the url in this mail?

* We can left click on the button and `Copy Link Location` to a notepad.

<figure><img src="../../../.gitbook/assets/3 (49).png" alt=""><figcaption></figcaption></figure>

* Since the question is asking for the domain name, we do not need the entire URL.

### Answer

```
storage.googleapis.com
```

##

## Question 3

> Is the domain mentioned in the previous question suspicious?

* Using [VirusTotal](https://www.virustotal.com/gui/home/search) we can check whether a URL is malicious or not.

<figure><img src="../../../.gitbook/assets/4 (42).png" alt=""><figcaption></figcaption></figure>

* It has been flagged as `Phishing` by `Abusix`.

### Answer

```
Yes
```

##

## Question 4

> What is the body SHA-256 of the domain?

```
$ curl storage.googleapis.com | sha256sum
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100   181  100   181    0     0   4309      0 --:--:-- --:--:-- --:--:--  4309
13945ecc33afee74ac7f72e1d5bb73050894356c4bf63d02a1a53e76830567f5  -
```

### Answer

```
13945ecc33afee74ac7f72e1d5bb73050894356c4bf63d02a1a53e76830567f5
```

##

## Question 5

> Is this email a phishing email?

* As we saw in the Virustotal analysis, the email is a phishing email.

### Answer

```
Yes
```

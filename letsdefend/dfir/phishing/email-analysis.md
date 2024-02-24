# Email Analysis

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}



## What is the sending email address?

Let's check the HTML source of the email.&#x20;

<figure><img src="../../../.gitbook/assets/1 (93).png" alt=""><figcaption></figcaption></figure>

The answer lies in the `From` field.

### Answer

```
yanting@united.com.sg
```



## What is the email address of the recipient?

The answer lies in the `To` field.&#x20;

<figure><img src="../../../.gitbook/assets/2 (90).png" alt=""><figcaption></figcaption></figure>

### Answer

```
admin@malware-traffic-analysis.net
```



## What is the subject line of the email?

The answer lies in the `Subject` field.&#x20;

<figure><img src="../../../.gitbook/assets/3 (77).png" alt=""><figcaption></figcaption></figure>

### Answer

```
united scientific equipment
```



## What date was the Email sent? Date format: MM/DD/YYYY

The answer lies in the `Date` field.&#x20;

<figure><img src="../../../.gitbook/assets/4 (61).png" alt=""><figcaption></figcaption></figure>

The answer should be in MM/DD/YYYY format.

### Answer

```
02/08/2021
```



## What is the originating IP?

The answer lies in the `Received` field.

<figure><img src="../../../.gitbook/assets/5 (55).png" alt=""><figcaption></figcaption></figure>

### Answer

```
71.19.248.52
```



## What country is the ip address from?

We can use IPData to lookup the location and threat profile of the IP address.&#x20;

<figure><img src="../../../.gitbook/assets/6 (47).png" alt=""><figcaption></figcaption></figure>

### Answer

```
Canada
```



## What is the name of the attachment when you unzip it? (with extension)

Let's unzip the attachment.

```
$ unzip united+scientific+equipent.zip 
Archive:  united+scientific+equipent.zip
[united+scientific+equipent.zip] united scientific equipent.exe password: 
  inflating: united scientific equipent.exe  
```

### Answer

```
united scientific equipent.exe 
```



## What is the sha256 hash of the File?

We can use the `sha256sum` utility to find the hash of the attachment file.

```
$ sha256sum 'united scientific equipent.exe'
9909753bfb0ac8ab165bab3555233d03b01a9274a92e57c022f87ccbe51ca415  united scientific equipent.exe
```

### Answer

```
9909753bfb0ac8ab165bab3555233d03b01a9274a92e57c022f87ccbe51ca415
```



## Is the email attachment malicious? Yes/No

We can use Virustotal to check if a file is malicious or not by simply entering the SHA256 hash we generated.

<figure><img src="../../../.gitbook/assets/7 (36).png" alt=""><figcaption></figcaption></figure>

### Answer

```
Yes
```

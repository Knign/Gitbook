# Simple Steganography

> Think the flag is somewhere in there. Would you help me find it? hint-" Steghide Might be Helpfull"&#x20;
>
> [Minions1.jpeg](https://ctflearn.com/challenge/download/894)&#x20;

Let's use the `strings` utility to extract the strings in the image file.

```
$ strings Minions1.jpeg | head
JFIF
0Photoshop 3.0
8BIM
myadmin
!1#%)+...
383-7(-.+
&/-/-//-++------------------------+---.-----/------
$3br
%&'()*456789:CDEFGHIJSTUVWXYZcdefghijstuvwxyz
```

The `steghide` utility allows users to extract data from image and audio files.

```
$ steghide extract -sf Minions1.jpeg
Enter passphrase:
wrote extracted data to "raw.txt".
```

* We can now use the `cat` command to view the contents of the extracted file.

```
$ cat raw.txt
AEMAVABGAGwAZQBhAHIAbgB7AHQAaABpAHMAXwBpAHMAXwBmAHUAbgB9
```

* That looks like it is encrypted using Base64. Let's decode it using [CyberChef](https://gchq.github.io/CyberChef/).

<figure><img src="../../.gitbook/assets/1 (63).png" alt=""><figcaption></figcaption></figure>

### Flag

```
CTFlearn{This_is_fun}
```

# Forensics 101

> Think the flag is somewhere in there. Would you help me find it? https://mega.nz/#!OHohCbTa!wbg60PARf4u6E6juuvK9-aDRe\_bgEL937VO01EImM7c

Let's open the link and see what is in the MEGA folder.

<figure><img src="../../.gitbook/assets/1 (76).png" alt=""><figcaption></figcaption></figure>

It's an image with a Minion on it. It also has some text but none of it is in the format of our flag.

There are some strings inside of an image file as well. These strings can be extracted using the `strings` utility in Linux.

```
$ strings 95f6edfb66ef42d774a5a34581f19052.jpg 
-- snip --;
flag{wow!_data_is_cool}
-- snip --;
```

Alternatively we can also use the `Strings` operation inside [Cyberchef](https://gchq.github.io/CyberChef/) in order to find the flag.&#x20;

<figure><img src="../../.gitbook/assets/2 (73).png" alt=""><figcaption></figcaption></figure>

### Flag

```
flag{wow!_data_is_cool}
```

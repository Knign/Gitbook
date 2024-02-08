# Emprisa Maldoc

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}

##

> Q1. What is the CVE ID of the exploited vulnerability?

* Let's find the file hash using `md5sum`.

```
$ md5sum c39-EmprisaMaldoc.rtf 
d82341600606afcf027646ea42f285ae  c39-EmprisaMaldoc.rtf
```

* We can search the file hash or just open the file in VirusTotal in order to find the CVE ID.

<figure><img src="../.gitbook/assets/emprisa 1.png" alt=""><figcaption></figcaption></figure>

##

> Q2. To reproduce the exploit in a lab environment and mimic a corporate machine running Microsoft office 2007, a specific patch should not be installed. Provide the patch number.

* Microsoft released a patch in 2017 for this vulnerability.

<figure><img src="../.gitbook/assets/emprisa 2.png" alt=""><figcaption></figcaption></figure>

* We can see the patch number mentioned in Method 3.

##

> Q3. What is the magic signature in the object data?

* The `rtfdump` tool help with this task.

```
$ rtfdump.py c39-EmprisaMaldoc.rtf 
    1 Level  1        c=    3 p=00000000 l=    8238 h=    7903;    4678 b=       0   u=      17 \rtf1
    2  Level  2       c=    1 p=00000034 l=      37 h=       3;       2 b=       0   u=       5 \fonttbl
    3   Level  3      c=    0 p=0000003d l=      27 h=       3;       2 b=       0   u=       5 \f0
    4  Level  2       c=    0 p=0000005c l=      30 h=      11;       4 b=       0   u=       5 \*\generator
    5  Level  2       c=    3 p=000000b2 l=    8054 h=    7889;    4678 b=       0   u=       7 \object
    6   Level  3      c=    0 p=000000cb l=      22 h=       3;       1 b=       0   u=       7 \*\objclass Equation.3
    7   Level  3      c=    0 p=000000f3 l=    7267 h=    7254;    4678 b=       0 O u=       0 \*\objdata
      Name: b'Equation.3\x00' Size: 3584 md5: 86e11891181069b51cc3d33521af9f1e magic: d0cf11e0
    8   Level  3      c=    1 p=00001d58 l=     719 h=     632;      78 b=       0   u=       0 \result
    9    Level  4     c=    1 p=00001d60 l=     710 h=     632;      78 b=       0   u=       0 \pict
   10     Level  5    c=    0 p=00001d66 l=      10 h=       0;       0 b=       0   u=       0 \*\picprop
   11 Remainder       c=    0 p=00002030 l=       1 h=       0;       0 b=       0   u=       0 
      Only whitespace = 1
```

##

> Q4. What is the name of the spawned process when the document gets opened?

* On opening the file with Any.Run, we can see that there is `EQNEDT32.EXE` process.&#x20;

<figure><img src="../.gitbook/assets/emprisa 4.png" alt=""><figcaption></figcaption></figure>

* This process makes connections with a Github account which is malicious behaviour.

##

> Q5. What is the full path of the downloaded payload?

```
$ rtfobj -s 0 c39-EmprisaMaldoc.rtf
```

```
$ strings c39-EmprisaMaldoc.rtf_object_000000FE.bin
Microsoft Equation 3.0
DS Equation
Equation.3
8GetPu
rocAu
ddreu
Qh.exehC:\oSRQharyAhLibrhLoadTS
YPQf
llQhon.dhurlmT
eAQ3
hoFilhoadThownlhURLDTP
T$$QQR
Z[SRQhxeca
hWinETS
Z[hessa
ahProchExitTS
https://raw.githubusercontent.com/accidentalrebel/accidentalrebel.com/gh-pages/theme/images/test.png
```

##

> Q6. Where is the URL used to fetch the payload?

* The answer is present in the final line of the last command output.

```
$ strings c39-EmprisaMaldoc.rtf_object_000000FE.bin
--snip--;
https://raw.githubusercontent.com/accidentalrebel/accidentalrebel.com/gh-pages/theme/images/test.png
```

##

> Q7. What is the flag inside the payload?

* Let's download the file from the URL we found for the previous question. We can use `wget` or `curl` for this task.

```
$ wget https://raw.githubusercontent.com/accidentalrebel/accidentalrebel.com/gh-pages/theme/images/test.png
--2023-07-21 11:33:41--  https://raw.githubusercontent.com/accidentalrebel/accidentalrebel.com/gh-pages/theme/images/test.png
Resolving raw.githubusercontent.com (raw.githubusercontent.com)... 185.199.110.133, 185.199.108.133, 185.199.111.133, ...
Connecting to raw.githubusercontent.com (raw.githubusercontent.com)|185.199.110.133|:443... connected.
HTTP request sent, awaiting response... 404 Not Found
Saving to: ‘test.png’

test.png                                             100%[=====================================================================================================================>]      14  --.-KB/s    in 0s      

2023-07-21 11:33:42 ERROR 404: Not Found.
```

* Then we can `grep` for the word `flag` piped with the `strings` command.


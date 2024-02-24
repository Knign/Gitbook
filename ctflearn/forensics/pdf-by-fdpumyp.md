# PDF by fdpumyp

> Hi, just as we talked during a break, you have this file here and check if something is wrong with it. That's the only thing we found strange with this suspect, I hope there will be a password for his external drive&#x20;
>
> Bye&#x20;
>
> [dontopen.pdf](https://ctflearn.com/challenge/download/957)

<figure><img src="../../.gitbook/assets/1 (62).png" alt=""><figcaption></figcaption></figure>

Opening the PDF doesn't give us anything of importance.

Let's use the `strings` utility to view all the strings present in the file.

```
$ strings dontopen.pdf | tail -15
== SECRET DATA DONT LOOK AT THIS ==
external:Q1RGbGVhcm57KV8xbDB3M3kwVW0wMG15MTIzfQ==
pin:1234
password:MTIzMVdST05HOWlzamRuUEFTU1dPUkQ=
endstream
endobj
xref
0000149877 00000 n
13 1
0000150079 00000 n
trailer
<</Size 14/Root 8 0 R/Info 1 0 R/Prev 149539>>
startxref
150295
%%EOF
```

The `external` and `password` fields look like they are Base64 encoded. We can decode them using [CyberChef](https://gchq.github.io/CyberChef/).

<figure><img src="../../.gitbook/assets/2 (60).png" alt=""><figcaption></figcaption></figure>

### Flag

```
CTFlearn{)_1l0w3y0Um00my123}
```

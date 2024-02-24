# HoneyBOT

{% hint style="warning" %}
Always open malware in a secure environment like a VM.
{% endhint %}

{% hint style="info" %}
We will be using the [REMnux](https://remnux.org/) distribution which is specifically made for reverse engineering.
{% endhint %}

##

> Q1. What is the attacker's IP address?

* We can see that the `Source address` field of the first packet is `98.114.205.102`.

<figure><img src="../.gitbook/assets/HoneyBOT 1.png" alt=""><figcaption></figcaption></figure>

##

> Q2. What is the target's IP address?

* The target's IP address is included in the `Destination address` field.

<figure><img src="../.gitbook/assets/HoneyBOT 2 (1).png" alt=""><figcaption></figcaption></figure>

##

> Q3. Provide the country code for the attacker's IP address (a.k.a geo-location).

* We can obtain more information about the attacker's IP address using [IPinfo](https://ipinfo.io/).&#x20;

<figure><img src="../.gitbook/assets/HoneyBOT 3 (1).png" alt=""><figcaption></figcaption></figure>

##

> Q4. How many TCP sessions are present in the captured traffic?

* We can find TCP sessions by selecting the `Statistics > Conversations` option.

<figure><img src="../.gitbook/assets/HoneyBOT 4 2.png" alt=""><figcaption></figcaption></figure>

* We can see that there are 5 TCP sessions present.

##

> Q5. How long did it take to perform the attack (in seconds)?

* Let us set the time display format to `Seconds since beginning of capture`.

<figure><img src="../.gitbook/assets/HoneyBOT 5.png" alt=""><figcaption></figcaption></figure>

* We can see that the last packet arrives around 16 seconds after the first packet. So it took 16 seconds to perform the attack.

##

{% hint style="info" %}
For some reason there is no question number 6.
{% endhint %}

##

> Q7. Provide the CVE number of the exploited vulnerability.

* Using the following filter we can filter out SMB packets.

```
smb
```

* On observing the packets, we can see a few DSSETUP packets. These are used to obtain information about a remote hosts Active Directory.

<figure><img src="../.gitbook/assets/HoneyBOT 7.png" alt=""><figcaption></figcaption></figure>

* The `Operation` field is set to `DsRoleUpgradeDownlevelServer`.
* A quick google search gives us the CVE number of the exploited vulnerability.

<figure><img src="../.gitbook/assets/HoneyBOT 7 2.png" alt=""><figcaption></figcaption></figure>

* It exploits a buffer overflow which in turn allows the attacker to perform [ACE](https://en.wikipedia.org/wiki/Arbitrary\_code\_execution) in order to create long debug entries.

##

> Q8. Which protocol was used to carry over the exploit?

* As we saw in the previous question, the protocol used was SMB.

##

> Q9. Which protocol did the attacker use to download additional malicious files to the target system?

* Let us follow the stream through `Analyze > Follow > TCP Stream`.
* On checking the 3rd TCP stream we can see the steps performed by the attacker.

<figure><img src="../.gitbook/assets/HoneyBOT 9.png" alt=""><figcaption></figcaption></figure>

* These steps resemble that of a [FTP login sequence](https://www.ibm.com/docs/en/zos/2.2.0?topic=ftp-logging-in).

<figure><img src="../.gitbook/assets/HoneyBOT 9 2.png" alt=""><figcaption></figcaption></figure>

* Alternatively, in TCP stream 2 we can see the command executed by the attacker.

<figure><img src="../.gitbook/assets/HoneyBOT 9 3.png" alt=""><figcaption></figcaption></figure>

* The attacker ran the `ftp` command using the script file `o` and disabled auto-login using the `n` flag.

##

> Q10. What is the name of the downloaded malware?

* Again in TCP stream 3 we can see that the attacker retrieved the copy of the `ssms.exe` file.

<figure><img src="../.gitbook/assets/HoneyBOT 10 2 (1).png" alt=""><figcaption></figcaption></figure>

* In TCP stream 2 we can see that the attacker executed the `ssms.exe` file.

<figure><img src="../.gitbook/assets/HoneyBOT 10 2.png" alt=""><figcaption></figcaption></figure>

##

> Q11. The attacker's server was listening on a specific port. Provide the port number.

* In the 2nd TCP stream, we can see port `8884` specified in the `echo` command.

<figure><img src="../.gitbook/assets/HoneyBOT 11.png" alt=""><figcaption></figcaption></figure>

* The result of this command is redirected into the script file `o` used during FTP login.

##

> Q12. When was the involved malware first submitted to VirusTotal for analysis? Format: YYYY-MM-DD

* TCP stream 4 contains the file sent from the attacker to the victim.

<figure><img src="../.gitbook/assets/HoneyBOT 12.png" alt=""><figcaption></figcaption></figure>

* We can download this file in the raw format via `Save as... > Raw`.
* Using the `md5sum` command we can find the hash of the saved file.

```
$ md5sum malware 
14a09a48ad23fe0ea5a180bee8cb750a  malware
```

* We can now search up this file hash using [VirusTotal](https://www.virustotal.com/gui/home/upload).&#x20;

<figure><img src="../.gitbook/assets/HoneyBOT 12 2.png" alt=""><figcaption></figcaption></figure>

##

> Q13. What is the key used to encode the shellcode?

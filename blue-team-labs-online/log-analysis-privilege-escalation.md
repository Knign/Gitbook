# Log Analysis - Privilege Escalation

## What user (other than ‘root’) is present on the server?

We can see the user move to a directory called `/home/daniel/`.

<figure><img src="../.gitbook/assets/1 (71).png" alt=""><figcaption></figcaption></figure>

### Answer

```
daniel
```



## What script did the attacker try to download to the server?

The attacker used the `wget` utility to download a Github script.

<figure><img src="../.gitbook/assets/2 (68).png" alt=""><figcaption></figcaption></figure>

## Answer

```
linux-exploit-suggester.sh
```



## What packet analyzer tool did the attacker try to use?

We can see the command `tcpdump` which is used for packet analysis on the command line.

<figure><img src="../.gitbook/assets/3 (63).png" alt=""><figcaption></figcaption></figure>

### Answer

```
tcpdump
```



## What file extension did the attacker use to bypass the file upload filter implemented by the developer?

The attacker tried to delete a file named `x.phtml`.

<figure><img src="../.gitbook/assets/4 (49).png" alt=""><figcaption></figcaption></figure>

The PHTML files contain PHP code that is parsed by a PHP engine which allows the web server to generate dynamic HTML that is displayed in a web browser.

### Answer

```
.phtml
```



## Based on the commands run by the attacker before removing the php shell, what misconfiguration was exploited in the ‘python’ binary to gain root-level access? 1- Reverse Shell ; 2- File Upload ; 3- File Write ; 4- SUID ; 5- Library load

We can see that the attacker tried to find binaries with the SUID bit set.

<figure><img src="../.gitbook/assets/5 (46).png" alt=""><figcaption></figcaption></figure>

On executing a binary with the SUID bit set, the file executes with the effective permissions of the owner of the file instead of the person executing. This allows for temporary privilege escalation.

Then the attacker executes `sh`.

<figure><img src="../.gitbook/assets/6 (43).png" alt=""><figcaption></figcaption></figure>

### Answer

```
4
```

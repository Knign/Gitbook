# Pickle Rick

{% embed url="https://tryhackme.com/room/picklerick" %}

##

## Task 1: Pickle Rick

### What is the first ingredient that Rick needs?

* Lets perform a simple `nmap` scan to see which ports are open.

```
$ nmap -sC -sV 10.10.88.164
Starting Nmap 7.92 ( https://nmap.org ) at 2023-11-11 14:52 IST
Nmap scan report for 10.10.88.164
Host is up (0.13s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.2p2 Ubuntu 4ubuntu2.6 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 b0:56:f1:d5:f7:ee:f0:9f:0f:9f:07:88:c6:56:7a:29 (RSA)
|   256 ef:9b:c2:3f:b3:84:8d:22:5e:d2:b4:09:59:ba:be:15 (ECDSA)
|_  256 0d:2a:4f:24:a0:9f:3d:20:80:31:b8:51:42:29:a7:0f (ED25519)
80/tcp open  http    Apache httpd 2.4.18 ((Ubuntu))
|_http-title: Rick is sup4r cool
|_http-server-header: Apache/2.4.18 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 25.91 seconds
```

* There are two open ports:

| Port | Service |
| ---- | ------- |
| 22   | ssh     |
| 80   | http    |

* Let's enter the IP address in the browser and see what comes up.&#x20;

<figure><img src="../../.gitbook/assets/2 (35).png" alt=""><figcaption></figcaption></figure>

* Let's check the page source for more information.

<figure><img src="../../.gitbook/assets/3 (33).png" alt=""><figcaption></figcaption></figure>

* So we have a username now: `R1ckRul3s`. However we don't know the password yet.
* On most websites, the `robots.txt` file does the job of disallowing web crawlers from accessing particular pages. Let's see if we can find anything there.&#x20;

<figure><img src="../../.gitbook/assets/4 (31).png" alt=""><figcaption></figcaption></figure>

* Looks like `Wubbalubbadubdub` is the password.
* But where should we enter these credentials?
* In order to find the login page we will have to perform some directory brute-forcing. There are various tools available, but in this case let's use `gobuster`.

```
$ gobuster dir -u http://10.10.88.164 -w /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt -x php
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.88.164
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/dirbuster/wordlists/directory-list-2.3-small.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Extensions:              php
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.php                 (Status: 403) [Size: 291]
/login.php            (Status: 200) [Size: 882]
/assets               (Status: 301) [Size: 313] [--> http://10.10.88.164/assets/]
/portal.php           (Status: 302) [Size: 0] [--> /login.php]
-- snip --;
```

* We can see a `/login.php` file. Let's go to the file in the browser.

<figure><img src="../../.gitbook/assets/5 (31).png" alt=""><figcaption></figcaption></figure>

* Let's enter the credentials that we found before i.e. `R1ckRul3s` as username and `Wubbalubbadubdub` as the password.

<figure><img src="../../.gitbook/assets/6 (32).png" alt=""><figcaption></figcaption></figure>

* We're in and we have a `Command Panel` to enter our commands.
* We can use the `ls` command to list the files and sub-directories.

<figure><img src="../../.gitbook/assets/7 (28).png" alt=""><figcaption></figcaption></figure>

* The `Sup3rS3cretPickl3Ingred.txt` file seems interesting. Let's `cat` the contents of that file.

<figure><img src="../../.gitbook/assets/8 (22).png" alt=""><figcaption></figcaption></figure>

* Oh! So `cat` is disabled. We have to find another way to read the file.
* We can `grep` all the contents of the file by using the `.` regular expression.

```
grep . Sup3rS3cretPickl3Ingred.txt
```

<figure><img src="../../.gitbook/assets/9 (16).png" alt=""><figcaption></figcaption></figure>

### Answer

```
mr. meeseek hair
```

##

### What is the second ingredient in Rick’s potion?

* We can check which user are present by using the following command:

```
cd /home ; ls
```

<figure><img src="../../.gitbook/assets/10 (13).png" alt=""><figcaption></figcaption></figure>

* Let's check what files `rick` has using the following command:

```
cd /home/rick ; ls
```

<figure><img src="../../.gitbook/assets/11 (5).png" alt=""><figcaption></figcaption></figure>

* Let's see what is in to the `second ingredients`.

```
grep . /home/rick/"second ingredients"
```

<figure><img src="../../.gitbook/assets/12 (2).png" alt=""><figcaption></figcaption></figure>

### Answer

```
1 jerry tear
```

##

### What is the last and final ingredient?

* Let's look at the `/root` directory using the following command:

```
sudo ls /root
```

<figure><img src="../../.gitbook/assets/13 (2).png" alt=""><figcaption></figcaption></figure>

* As always, we can use `grep` to read the contents of a file.

```
sudo grep . /root/3rd.txt
```

<figure><img src="../../.gitbook/assets/14 (2).png" alt=""><figcaption></figcaption></figure>

### Answer

```
fleeb juice
```

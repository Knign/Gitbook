# Anthem

{% embed url="https://tryhackme.com/room/anthem" %}

##

## Task 1: Website Analysis

<div align="center">

<figure><img src="../../.gitbook/assets/1 (117).png" alt=""><figcaption></figcaption></figure>

</div>

### Let's run nmap and check what ports are open.

{% code fullWidth="false" %}
```
$ nmap -sC -sV 10.10.5.238 
Starting Nmap 7.92 ( https://nmap.org ) at 2023-12-07 19:48 IST
Nmap scan report for 10.10.5.238
Host is up (0.14s latency).
Not shown: 998 filtered tcp ports (no-response)
PORT     STATE SERVICE       VERSION
80/tcp   open  http          Microsoft HTTPAPI httpd 2.0 (SSDP/UPnP)
3389/tcp open  ms-wbt-server Microsoft Terminal Services
| ssl-cert: Subject: commonName=WIN-LU09299160F
| Not valid before: 2023-12-06T14:18:23
|_Not valid after:  2024-06-06T14:18:23
|_ssl-date: 2023-12-07T14:20:35+00:00; +2s from scanner time.
| rdp-ntlm-info: 
|   Target_Name: WIN-LU09299160F
|   NetBIOS_Domain_Name: WIN-LU09299160F
|   NetBIOS_Computer_Name: WIN-LU09299160F
|   DNS_Domain_Name: WIN-LU09299160F
|   DNS_Computer_Name: WIN-LU09299160F
|   Product_Version: 10.0.17763
|_  System_Time: 2023-12-07T14:19:28+00:00
Service Info: OS: Windows; CPE: cpe:/o:microsoft:windows

Host script results:
|_clock-skew: mean: 1s, deviation: 0s, median: 1s

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 103.08 seconds

```
{% endcode %}

* There are two open ports:

| Port | Service       |
| ---- | ------------- |
| 80   | http          |
| 3389 | ms-wbt-server |

### No answer needed

###

### What port is for the web server?

* HTTP is the protocol for the web server.

### Answer

```
80
```

###

### What port is for remote desktop service?

* `ms-wbt-server` is the remote desktop service that runs on port 3389.

### Answer

```
3389
```

####

### What is a possible password in one of the pages web crawlers check for?

* The page that web crawlers check for is `robots.txt`. Let's see if that has something of importance.&#x20;

<figure><img src="../../.gitbook/assets/3 (94).png" alt=""><figcaption></figcaption></figure>

* The password is mentioned along with the disallowed pages.

### Answer

```
UmbracoIsTheBest!
```

####

### What CMS is the website using?

* We can find this answer on the `/robots.txt` page as well.&#x20;

<figure><img src="../../.gitbook/assets/4 (74).png" alt=""><figcaption></figcaption></figure>

* The `/umbraco/` page tells us that the CMS is Umbraco.

```
Umbraco
```

####

### What is the domain of the website?

* Let's visit the webpage of the target machine.

<figure><img src="../../.gitbook/assets/2 (109).png" alt=""><figcaption></figcaption></figure>

* Nothing really important here.
* In the second post, an email address is listed.

<figure><img src="../../.gitbook/assets/6 (25).png" alt=""><figcaption></figcaption></figure>

### Answer

```
anthem.com
```

###

### What's the name of the Administrator

* Let's check out the first blog post.

<figure><img src="../../.gitbook/assets/5 (62).png" alt=""><figcaption></figcaption></figure>

* We can see that there is a poem written about the admin. This poem is actually a real one written about Solomon Grundy.

### Answer

```
Solomon Grundy
```

###

### Can we find find the email address of the administrator?

* If we check out the second post, we can find the email format.&#x20;

<figure><img src="../../.gitbook/assets/6 (51).png" alt=""><figcaption></figcaption></figure>

* Now that we know the email of Jane Doe is `JD@anthem.com` we can guess Solomon Grundy's email address.

```
SG@anthem.com
```

##

## Task 2: Spot the Flags

### What is flag 1?

* We can find the first flag in the source page of the second post.

<figure><img src="../../.gitbook/assets/7 (41).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{L0L_WH0_US3S_M3T4}
```

###

### What is flag 2?

* We can find the second flag in the source page of the main web page.&#x20;

<figure><img src="../../.gitbook/assets/8 (30).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{G!T_G00D}
```

###

### What is flag 3?

* We can find the third flag on viewing Jane Doe's profile.

<figure><img src="../../.gitbook/assets/9 (22).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{L0L_WH0_D15}
```

###

### What is flag 4?

* We can find the fourth flag on the source page of the first post.

<figure><img src="../../.gitbook/assets/10 (17).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{AN0TH3R_M3TA}
```

##

## Task 3: Final stage

### Let's figure out the username and password to log in to the box.(The box is not on a domain)

* We know that there is a user `sg` and a password `UmbracoIsTheBest!`.

### No answer needed

###

### Gain initial access to the machine, what is the contents of user.txt?

* Using the credentials we can connect to the target through RDP.

```
$ xfreerdp /v:10.10.5.238 /u:sg /p:UmbracoIsTheBest! /cert:ignore +clipboard /dynamic-resolution
```

* After logging in, we can open the `user` file to get the flag.

<div data-full-width="false">

<figure><img src="../../.gitbook/assets/11 (8).png" alt=""><figcaption></figcaption></figure>

</div>

### Answer

```
THM{N00T_NO0T}
```

###

### Question

> Can we spot the admin password?

* After changing the `View` to `Show hidden items` we can go to `C\backup\`.
* There is file there which we don't have the permissions to read.

<figure><img src="../../.gitbook/assets/12 (5).png" alt=""><figcaption></figcaption></figure>

* Let's see if we can change the permissions.

<figure><img src="../../.gitbook/assets/13 (8).png" alt=""><figcaption></figcaption></figure>

* After changing the permissions, we can read the file.

<figure><img src="../../.gitbook/assets/14 (3).png" alt=""><figcaption></figcaption></figure>

### Answer

```
ChangeMeBaby1MoreTime
```

###

### Question

> Escalate your privileges to root, what is the contents of root.txt?

* Let's end the current RDP session and login again as `Administrator` with the password as `ChangeMeBaby1MoreTime`.

```
$ xfreerdp /v:10.10.5.238 /u:Administrator /p:ChangeMeBaby1MoreTime /cert:ignore +clipboard /dynamic-resolution
```

<figure><img src="../../.gitbook/assets/15 (2).png" alt=""><figcaption></figcaption></figure>

### Answer

```
THM{Y0U_4R3_1337}
```

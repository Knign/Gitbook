# Baby's First

> Reversing means reading code. Read this file, and find the flag!  [babysfirst.py](https://ctf.csaw.io/files/6199488bc907ef054b46816a1f3988de/babysfirst.py?token=eyJ1c2VyX2lkIjoxMzYwLCJ0ZWFtX2lkIjo1NjksImZpbGVfaWQiOjI3fQ.ZQSHWg.eB4nUrihe6bTD3GgMR9DRGUi1nU)

Let's download the file and check the code.

### Source code

```python
#!/usr/bin/env python3

# Reversing is hard. But....not always.
#
# Usually, you won't have access to source.
# Usually, these days, programmers are also smart enough not to include sensitive data in what they send to customers....
#
# But not always....

if input("What's the password? ") == "csawctf{w3_411_star7_5om3wher3}":
  print("Correct! Congrats! It gets much harder from here.")
else:
  print("Trying reading the code...")

# Notes for beginners:
#
# This is Python file. You can read about Python online, but it's a relatively simple programming language.
# You can run this from the terminal using the command `python3 babysfirst.py`, but I'll direct you to the internet again
# for how to use the terminal to accomplish that.
#
# Being able to run this file is not required to find the flag.
#
# You don't need to know Python to read this code, to guess what it does, or to solve the challenge.
```

We can see that the flag is mentioned as part of the code without any encryption or hashing.

### Flag

```
csawctf{w3_411_star7_5om3wher3}
```

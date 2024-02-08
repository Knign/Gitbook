---
cover: ../.gitbook/assets/oops.png
coverY: 0
---

# Oops I deleted my bin/ dir :(

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*1JI5gnXl4ocO7kMYbUsUKA.png" alt=""><figcaption><p><a href="https://oops.cmdchallenge.com/">https://oops.cmdchallenge.com/</a></p></figcaption></figure>

This is the write-up for the [**Oops I deleted my bin/ dir :(**](https://oops.cmdchallenge.com/) challenge. In this challenge we are only allowed to use the echo command.

***

> _**#1]**_** For now, all you need to do is figure out where you are,**\
> **print the current working directory.**

```
> pwd
```

***

> _**#2]**_** List all of the files on a single line, in the current working directory.**

```
> echo *
```

***

> _**#3]**_** Oh no! You now remember there is a very important file in this directory. Display its contents before the data is lost for forever!**

```
>echo "$(<my-dissertation.txt)"
```

***

> _**#4]**_** You know there is a process on machine that is deleting files, the first thing you want to do is identify the name of it. Print the name of the process**

```
> echo "$(</proc/42/cmdline)"
```

***

> _**#5]**_** You managed to save your important file. Now that you know the process name it will be good to kill it before it does any more damanage.**

```
> kill 42
```

***

This was a short but pretty challenging one.

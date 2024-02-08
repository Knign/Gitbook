---
cover: ../.gitbook/assets/twelve.png
coverY: 0
---

# Twelve Days of Shell

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*QgMAfqLDl7LKTzVN3Tk7qw.png" alt=""><figcaption><p><a href="https://12days.cmdchallenge.com/">https://12days.cmdchallenge.com/</a></p></figcaption></figure>

The prompts for the [Twelve Days of Shell](https://12days.cmdchallenge.com/) challenge are a bit cryptic.

***

> _**#1]**_** On the first day of Shell my true love gave to me**\
> **A list of files in the directory tree …**

```
> ls
```

***

> _**#2]**_** On the second day of Shell my true love gave to me**\
> **Two lines a-laughing …**

```
> cat night-before-christmas.txt | grep "laugh"
```

***

> _**#3]**_** On the third day of Shell my true love gave to me**\
> **Three lines at the beginning …**

```
> head -n 3 night-before-christmas.txt
```

***

> _**#4]**_** On the fourth day of Shell my true love gave to me**\
> **Four lines at the end …**

```
> tail -n 4 night-before-christmas.txt
```

***

> _**#5]**_** On just about every Unix and Unix-like operating systems there is a command named **_**`ls`**_**. **_**`ls`**_** is short for "list" and can be used to list files in your current working directory. Try sending the command **_**`ls`**_** in the command box to list all files in the directory.**

```
> cat night-before-christmas.txt | grep -i "^the" 
```

***

> _**#6]**_** On the sixth day of Shell my true love gave to me**\
> **Six lines that are exciting! …**

```
> cat night-before-christmas.txt | grep -i "!" 
```

***

> _**#7]**_** On the seventh day of Shell my true love gave to me**\
> **Seven files that start with “Santa” …**

```
> find Santa* 
```

***

> _**#8]**_** On the eighth day of Shell my true love gave to me**\
> **Eight elves in Santa’s Workhop/ …**

```
> mv Elves/* Workshop
```

***

> _**#9]**_** On the ninth day of Shell my true love gave to me**\
> **Nine names of Santa’s Reindeer …**

```
> find ./ -type f
```

***

> _**#10]**_** On the tenth day of Shell my true love gave to me**\
> **Ten Lords by their names sorted …**

```
> cat lords.txt | sort
```

***

> _**#11]**_** On the eleventh day of Shell my true love gave to me**\
> **Eleven lines with pipers ♫ piping ♫ …**

```
> find -name "piper" -exec grep piping {} \;
```

***

> _**#12]**_** On the eighth day of Shell my true love gave to me**\
> **Eight elves in Santa’s Workhop/ …**

```
> echo "$(<twelve-days-of-shell.txt)"
```

***

That concludes the challenge.

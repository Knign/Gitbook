# Twelve Days of Shell

**On the first day of Shell my true love gave to me**\
**A list of files in the directory tree …**
-------------------------------------------

```
> ls
```



**On the second day of Shell my true love gave to me**\
**Two lines a-laughing …**
--------------------------

```
> cat night-before-christmas.txt | grep "laugh"
```



**On the third day of Shell my true love gave to me**\
**Three lines at the beginning …**
----------------------------------

```
> head -n 3 night-before-christmas.txt
```



**On the fourth day of Shell my true love gave to me**\
**Four lines at the end …**
---------------------------

```
> tail -n 4 night-before-christmas.txt
```



## **On just about every Unix and Unix-like operating systems there is a command named **_**`ls`**_**. **_**`ls`**_** is short for "list" and can be used to list files in your current working directory. Try sending the command **_**`ls`**_** in the command box to list all files in the directory.**

```
> cat night-before-christmas.txt | grep -i "^the" 
```



**On the sixth day of Shell my true love gave to me**\
**Six lines that are exciting! …**
----------------------------------

```
> cat night-before-christmas.txt | grep -i "!" 
```



**On the seventh day of Shell my true love gave to me**\
**Seven files that start with “Santa” …**
-----------------------------------------

```
> find Santa* 
```



**On the eighth day of Shell my true love gave to me**\
**Eight elves in Santa’s Workhop/ …**
-------------------------------------

```
> mv Elves/* Workshop
```



**On the ninth day of Shell my true love gave to me**\
**Nine names of Santa’s Reindeer …**
------------------------------------

```
> find ./ -type f
```



**On the tenth day of Shell my true love gave to me**\
**Ten Lords by their names sorted …**
-------------------------------------

```
> cat lords.txt | sort
```



**On the eleventh day of Shell my true love gave to me**\
**Eleven lines with pipers ♫ piping ♫ …**
-----------------------------------------

```
> find -name "piper" -exec grep piping {} \;
```



**On the eighth day of Shell my true love gave to me**\
**Eight elves in Santa’s Workhop/ …**
-------------------------------------

```
> echo "$(<twelve-days-of-shell.txt)"
```

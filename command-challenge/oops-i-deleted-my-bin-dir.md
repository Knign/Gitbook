# Oops I deleted my bin/ dir :(

**For now, all you need to do is figure out where you are,**\
**print the current working directory.**
----------------------------------------

```
> pwd
```



## **List all of the files on a single line, in the current working directory.**

```
> echo *
```



## **Oh no! You now remember there is a very important file in this directory. Display its contents before the data is lost for forever!**

```
>echo "$(<my-dissertation.txt)"
```



## **You know there is a process on machine that is deleting files, the first thing you want to do is identify the name of it. Print the name of the process**

```
> echo "$(</proc/42/cmdline)"
```



## **You managed to save your important file. Now that you know the process name it will be good to kill it before it does any more damanage.**

```
> kill 42
```

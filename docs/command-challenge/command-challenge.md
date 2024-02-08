---
cover: ../.gitbook/assets/command chall.png
coverY: 0
---

# Command Challenge

<figure><img src="https://cdn-images-1.medium.com/max/1000/1*UAaENRvNv66CzuDVMc9s7A.png" alt=""><figcaption><p><a href="https://cmdchallenge.com/">https://cmdchallenge.com/</a></p></figcaption></figure>

I recently discovered a pretty cool website called [**Command Challenge**](https://cmdchallenge.com/). I went into it thinking it would be a breeze to get through but I got stuck plenty of times. I thought it would be cool to document the answers.

***

> _**#1]**_** Print “hello world” on the terminal in a single command.**

```
> echo “hello world”
```

***

> _**#2]**_** Print the current working directory.**

```
> pwd
```

***

> _**#3]**_** List names of all the files in the current directory, one file per line.**

```
> ls
```

***

> _**#4]**_** There is a file named access.log in the current directory. Print the contents.**

```
> cat access.log
```

***

> _**#5]**_** Print the last 5 lines of “access.log”.**

```
> tail -5 access.log
```

***

> _**#6]**_** Create an empty file named take-the-command-challenge in the current working directory.**

```
> touch take-the-command-challenge
```

***

> _**#7]**_** Create a directory named tmp/files in the current working directory**

```
> mkdir -p tmp/files
```

***

> _**#8]**_** Copy the file named take-the-command-challenge to the directory tmp/files**

```
> cp take-the-command-challenge ./tmp/files/
```

***

> _**#9]**_** Move the file named take-the-command-challenge to the directory tmp/files.**

```
> mv take-the-command-challenge ./tmp/files/
```

***

> _**#10]**_** Create a symbolic link named take-the-command-challenge that points to the file tmp/files/take-the-command-challenge.**

```
> ln -s tmp/files/take-the-command-challenge
```

***

> _**#11]**_** Delete all of the files in this challenge directory including all subdirectories and their contents.**

```
> rm -r * .*
```

***

> _**#12]**_** There are files in this challenge with different file extensions.**\
> **Remove all files with the .doc extension recursively in the current working directory.**

```
> rm -r **/*.doc
```

***

> _**#13]**_** There is a file named `access.log` in the current working directory. Print all lines in this file that contains the string "GET".**

```
> grep "GET" access.log
```

***

> _**#14]**_** Print all files in the current directory, one per line (not the path, just the filename) that contain the string “500”.**

```
>  grep -l "500" *
```

***

> _**#15]**_** Print the relative file paths, one path per line for all filenames that start with “access.log” in the current directory.**

```
> ls *access.log*
```

***

> _**#16]**_** Print all matching lines (without the filename or the file path) in all files under the current directory that start with “access.log” that contain the string “500”.**

```
> grep -rh "500"
```

***

> _**#17]**_** Extract all IP addresses from files that start with “access.log” printing one IP address per line.**

```
> grep -ro ^[0-9.]*
```

***

> _**#18]**_** Count the number of files in the current working directory. Print the number of files as a single integer.**

```
> ls -A | wc -l 
```

***

> _**#19]**_** Print the contents of access.log sorted.**

```
> cat access.log | sort 
```

***

> _**#20]**_** Print the number of lines in access.log that contain the string “GET”.**

```
> grep "GET" access.log | wc -l
```

***

> _**#21]**_** The file split-me.txt contains a list of numbers separated by a `;` character. Split the numbers on the `;` character, one number per line.**

```
> cat split-me.txt |tr ';' "\n"
```

***

> **#22] Print the numbers 1 to 100 separated by spaces.**

```
> echo {1..100};
```

***

> _**#23]**_** This challenge has text files (with a .txt extension) that contain the phrase “challenges are difficult”. Delete this phrase from all text files recursively.**

```
> sed -i "challenges are difficult" **/*.txt
```

***

> _**#24]**_** The file sum-me.txt has a list of numbers, one per line. Print the sum of these numbers.**

```
> cat sum-me.txt|paste -sd+|bc
```

***

> _**#25]**_** Print all files in the current directory recursively without the leading directory path.**

```
> find -type f -printf  "%f\n"
```

***

> _**#26]**_** Rename all files removing the extension from them in the current directory recursively.**

```
> rm -rf *
```

***

> _**#27]**_** The files in this challenge contain spaces. List all of the files (filenames only) in the current directory but replace all spaces with a ‘.’ character.**

```
> ls | tr ' ' '.'
```

***

> _**#28]**_** In this challenge there are some directories containing files with different extensions. Print all directories, one per line without duplicates that contain one or more files with a “.tf” extension.**

```
> dirname **/*.tf | sort -u
```

***

> _**#29]**_** There are a mix of files in this directory that start with letters and numbers. Print the filenames (just the filenames) of all files that start with a number recursively in the current directory.**

```
> find -type f -printf '%f\n' | grep ^[0-9]
```

***

> _**#30]**_** Print the 25th line of the file faces.txt**

```
> head -25 faces.txt | tail -1
```

***

> _**#31]**_** Print the lines of the file `reverse-me.txt` in this directory in reverse line order so that the last line is printed first and the first line is printed last.**

```
> tac reverse-me.txt
```

***

> _**#32]**_** Print the file faces.txt, but only print the first instance of each duplicate line, even if the duplicates don’t appear next to each other.**

```
> cat -n faces.txt | sort -u -k 2 | sort -n | cut -f 2
```

***

> _**#33]**_** The file random-numbers.txt contains a list of 100 random integers.**\
> **Print the number of unique prime numbers contained in the file.**

```
> cat random-numbers.txt | sort | uniq | factor | awk "NF==2" | wc -l
```

***

> _**#34]**_** access.log.1 and access.log.2 are http server logs. Print the IP addresses common to both files, one per line.**

```
> awk 'a[$1]++ {print $1}' {access.log.1,access.log.2}
```

***

> _**#35]**_** Print all matching lines (without the filename or the file path) in all files under the current directory that start with “access.log”, where the next line contains the string “404”.**

```
> grep -h -B1 404 **/access.log* | grep -vE '404|--'
```

***

> _**#36]**_** Print all files with a `.bin` extension in the current directory that are different than the file named base.bin.**

```
> diff *.bin --to-file=base.bin | cut -d ' ' -f3
```

***

> _**#37]**_** There is a file: `./.../ /. .the flag.txt` Show its contents on the screen.**

```
> cat './.../  /. .the flag.txt'
```

***

> _**#38]**_** How many lines contain tab characters in the file named `file-with-tabs.txt` in the current directory.**

```
> grep -P "\t" * | wc -l
```

***

> _**#39]**_** There are files in this challenge with different file extensions. Remove all files without the .txt and .exe extensions recursively in the current working directory.**

```
> find -type f ! -regex '.*\(exe\|txt\)$' -delete
```

***

> _**#40]**_** There are some files in this directory that start with a dash in the filename. Remove those files.**

```
> rm ./-*
```

***

> _**#41]**_** There are two files in this directory, ps-ef1 and ps-ef2. Print the contents of both files sorted by PID and delete repeated lines.**

```
> cat ps-* | sort -k2 -n | uniq
```

***

> _**#42]**_** In the current directory there is a file called netstat.out. Print all the IPv4 listening ports sorted from the higher to lower.**

```
> cat netstat.out | grep -w "LISTEN" | awk '{print $4}' | cut -d":" -f2 |  sort -rn
```

***

That concludes the challenge.

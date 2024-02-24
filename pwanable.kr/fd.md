# fd

> Mommy! what is a file descriptor in Linux?

Let's figure out how the program works.

```c
#include <stdio.h>
#include <stdlib.h>
#include <string.h>
char buf[32];
int main(int argc, char* argv[], char* envp[]){
        if(argc<2){
                printf("pass argv[1] a number\n");
                return 0;
        }
        int fd = atoi( argv[1] ) - 0x1234;
        int len = 0;
        len = read(fd, buf, 32);
        if(!strcmp("LETMEWIN\n", buf)){
                printf("good job :)\n");
                system("/bin/cat flag");
                exit(0);
        }
        printf("learn about Linux file IO\n");
        return 0;

}
```

The program checks to see if we have passed to arguments or not.

It the converts our second argument into an integer using `atoi`, subtracts 0x1234 from it and then stores the value in `fd`.

It then reads 32 bytes from the file descriptor `fd` into the buffer `buf`.

If the string that is read is "LETMEWIN", it cats out the flag.

Knowing all this, we have to provide the second argument such that when subtracted by `0x1234` the answer is `0` (0 is the file descriptor for STDIN).

`0x1234` in decimal is `4660`.

When we provide the arguments the program reads input from STDIN.

```
fd@pwnable:~$ ./fd 4660
LETMEWIN
good job :)
mommy! I think I know what a file descriptor is!!
```

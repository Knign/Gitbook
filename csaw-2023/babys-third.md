# Baby's Third

> Babies can't count, but they can do binaries?&#x20;
>
> Author: `ElykDeer`&#x20;
>
> [readme.txt](https://ctf.csaw.io/files/756fbe5199cd02ce3375d9a36d8810b9/readme.txt?token=eyJ1c2VyX2lkIjoxMzYwLCJ0ZWFtX2lkIjo1NjksImZpbGVfaWQiOjI4fQ.ZQSQiA.tIYkx\_pUyC0S-t83fkEIuA13QWE) [babysthird](https://ctf.csaw.io/files/535cc4a217b7e7e1b56fd88645690d28/babysthird?token=eyJ1c2VyX2lkIjoxMzYwLCJ0ZWFtX2lkIjo1NjksImZpbGVfaWQiOjI5fQ.ZQSQiA.IdOLa1q6rsSXNEfDFVbEzSXAGGU)

I first ran the binary in order to see what it does.

```
$ ./babysthird
Enter your password:
```

Using the `checksec` utility, I saw the security properties of the file.

```
$ checksec babysthird 
[*] '/home/hacker/csaw23/babysThird/babysthird'
    Arch:     amd64-64-little
    RELRO:    Full RELRO
    Stack:    Canary found
    NX:       NX enabled
    PIE:      PIE enabled
```

* There's two important properties here:
  * `NX enabled`: This means that the stack is not executable. Therefore we cannot use a shellcode injection.
  * `PIE enabled`: This means that the executable is positionally independent. So the code and memory regions will have the same address every time we run it.
* Before disassembling the executable, I opened the `readme.txt` file and saw an interesting line.

```
Most notably, binutils includes `objdump` and `strings`. One of those are what you need to solve this challenge...
```

* So, then I used the `strings` utility to see if the flag was stored somewhere in plaintext.

```
$ strings babysthird 
/lib64/ld-linux-x86-64.so.2
__cxa_finalize
__libc_start_main
strcmp
puts
__isoc99_scanf
__stack_chk_fail
printf
libc.so.6
GLIBC_2.7
GLIBC_2.4
GLIBC_2.2.5
GLIBC_2.34
_ITM_deregisterTMCloneTable
__gmon_start__
_ITM_registerTMCloneTable
PTE1
u+UH
Enter your password: 
%99s
csawctf{st1ng_th30ry_a1nt_so_h4rd}
Correct!
Access denied.
:*3$"
GCC: (Ubuntu 11.4.0-1ubuntu1~22.04) 11.4.0
Scrt1.o
__abi_tag
crtstuff.c
deregister_tm_clones
__do_global_dtors_aux
completed.0
__do_global_dtors_aux_fini_array_entry
frame_dummy
__frame_dummy_init_array_entry
babysthird.c
__FRAME_END__
_DYNAMIC
__GNU_EH_FRAME_HDR
_GLOBAL_OFFSET_TABLE_
__libc_start_main@GLIBC_2.34
_ITM_deregisterTMCloneTable
puts@GLIBC_2.2.5
_edata
_fini
__stack_chk_fail@GLIBC_2.4
printf@GLIBC_2.2.5
__data_start
strcmp@GLIBC_2.2.5
__gmon_start__
__dso_handle
_IO_stdin_used
_end
__bss_start
main
__isoc99_scanf@GLIBC_2.7
__TMC_END__
_ITM_registerTMCloneTable
__cxa_finalize@GLIBC_2.2.5
_init
.symtab
.strtab
.shstrtab
.interp
.note.gnu.property
.note.gnu.build-id
.note.ABI-tag
.gnu.hash
.dynsym
.dynstr
.gnu.version
.gnu.version_r
.rela.dyn
.rela.plt
.init
.plt.got
.plt.sec
.text
.fini
.rodata
.eh_frame_hdr
.eh_frame
.init_array
.fini_array
.dynamic
.data
.bss
.comment
```

And there was the flag!

### Flag

```
csawctf{st1ng_th30ry_a1nt_so_h4rd}
```

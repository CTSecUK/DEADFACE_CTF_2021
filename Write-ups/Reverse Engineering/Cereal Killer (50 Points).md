# Cereal Killer

![Category](http://img.shields.io/badge/Category-Reverse_Engineering-orange?style=for-the-badge) ![Points](http://img.shields.io/badge/Points-50-brightgreen?style=for-the-badge)

## Details

> ![image](https://user-images.githubusercontent.com/73170900/137821256-df7966fe-b006-4d14-8b35-a0eab0b2d12f.png)
>
> spookyboi is really into Serial Killers. He loves to watch Mindhunter on NetFlix. He can also SLAY a bowl of his favorite cereal.
> 
> (Choose either the Windows or Linux binaries to analyze...)
> 
> [RE01 (Windows)](https://tinyurl.com/wz2rt9y5)
> 
> SHA1: 3674964b75d2894f297470be8a39802af40314b3
> 
> [RE01 (Linux)](https://tinyurl.com/sj75xk2r)
> 
> SHA1: af2392a43e3571fa43be6a48a3a83131f549013c
---

To solve this challenge we can use gdb (which i use with [pwndbg plug-in](https://github.com/pwndbg/pwndbg))

```assembly
❯ gdb deadface_re01.bin
GNU gdb (GDB) 11.1
Copyright (C) 2021 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.
Type "show copying" and "show warranty" for details.
This GDB was configured as "x86_64-pc-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<https://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
    <http://www.gnu.org/software/gdb/documentation/>.

For help, type "help".
Type "apropos word" to search for commands related to "word"...
pwndbg: loaded 190 commands. Type pwndbg [filter] for a list.
pwndbg: created $rebase, $ida gdb functions (can be used with print/break)
Reading symbols from deadface_re01.bin...
(No debugging symbols found in deadface_re01.bin)
pwndbg> 
```

Running the program we see;

```assembly
pwndbg> run
Starting program: /home/jaxigt/Downloads/deadface_re01.bin 
ERROR: Could not find ELF base!
What is the best and sp00kiest breakfast cereal?
Please enter the passphrase: 123
notflag{you-guessed-it---this-is-not-the-flag}
[Inferior 1 (process 6160) exited normally]
```

```assembly 
pwndbg> disassemble main
Dump of assembler code for function main:
   0x00005555555550c0 <+0>:     endbr64 
   0x00005555555550c4 <+4>:     push   rbx
   0x00005555555550c5 <+5>:     lea    rcx,[rip+0xf3c]        # 0x555555556008
   0x00005555555550cc <+12>:    sub    rsp,0x230
   0x00005555555550d3 <+19>:    mov    rax,QWORD PTR fs:0x28
   0x00005555555550dc <+28>:    mov    QWORD PTR [rsp+0x228],rax
   0x00005555555550e4 <+36>:    xor    eax,eax
   0x00005555555550e6 <+38>:    cs nop WORD PTR [rax+rax*1+0x0]
   0x00005555555550f0 <+48>:    movzx  edx,BYTE PTR [rcx+rax*1]
   0x00005555555550f4 <+52>:    test   dl,dl
   0x00005555555550f6 <+54>:    je     0x5555555550fe <main+62>
   0x00005555555550f8 <+56>:    xor    edx,0x5a
   0x00005555555550fb <+59>:    mov    BYTE PTR [rsp+rax*1],dl
   0x00005555555550fe <+62>:    add    rax,0x1
   0x0000555555555102 <+66>:    cmp    rax,0x1f
   0x0000555555555106 <+70>:    jne    0x5555555550f0 <main+48>
   0x0000555555555108 <+72>:    lea    rdi,[rip+0xf19]        # 0x555555556028
   0x000055555555510f <+79>:    mov    BYTE PTR [rsp+0x1e],0x0
   0x0000555555555114 <+84>:    lea    rbx,[rsp+0x20]
   0x0000555555555119 <+89>:    call   0x555555555080 <puts@plt>
   0x000055555555511e <+94>:    lea    rdx,[rip+0xf6a]        # 0x55555555608f
   0x0000555555555125 <+101>:   lea    rsi,[rip+0xf81]        # 0x5555555560ad
   0x000055555555512c <+108>:   xor    eax,eax
   0x000055555555512e <+110>:   mov    edi,0x1
   0x0000555555555133 <+115>:   call   0x5555555550a0 <__printf_chk@plt>
   0x0000555555555138 <+120>:   mov    rsi,rbx
   0x000055555555513b <+123>:   lea    rdi,[rip+0xf6b]        # 0x5555555560ad
   0x0000555555555142 <+130>:   xor    eax,eax
   0x0000555555555144 <+132>:   call   0x5555555550b0 <__isoc99_scanf@plt>
   0x0000555555555149 <+137>:   movabs rax,0x68632d746e753063
   0x0000555555555153 <+147>:   cmp    QWORD PTR [rsp+0x20],rax
   0x0000555555555158 <+152>:   je     0x555555555184 <main+196>
   0x000055555555515a <+154>:   lea    rdi,[rip+0xeff]        # 0x555555556060
   0x0000555555555161 <+161>:   call   0x555555555080 <puts@plt>
   0x0000555555555166 <+166>:   mov    rax,QWORD PTR [rsp+0x228]
   0x000055555555516e <+174>:   xor    rax,QWORD PTR fs:0x28
   0x0000555555555177 <+183>:   jne    0x55555555519f <main+223>
   0x0000555555555179 <+185>:   add    rsp,0x230
   0x0000555555555180 <+192>:   xor    eax,eax
   0x0000555555555182 <+194>:   pop    rbx
   0x0000555555555183 <+195>:   ret    
   0x0000555555555184 <+196>:   cmp    DWORD PTR [rsp+0x28],0x6c756330
   0x000055555555518c <+204>:   jne    0x55555555515a <main+154>
   0x000055555555518e <+206>:   cmp    WORD PTR [rbx+0xc],0x61
   0x0000555555555193 <+211>:   jne    0x55555555515a <main+154>
   0x0000555555555195 <+213>:   mov    rdi,rsp
   0x0000555555555198 <+216>:   call   0x555555555080 <puts@plt>
   0x000055555555519d <+221>:   jmp    0x555555555166 <main+166>
   0x000055555555519f <+223>:   call   0x555555555090 <__stack_chk_fail@plt>
End of assembler dump.
```

```assembly
0x0000555555555153 <+147>:   cmp    QWORD PTR [rsp+0x20],rax
```

```
pwndbg> break *0x0000555555555153
Breakpoint 1 at 0x555555555153
```

```assembly
pwndbg> run
Starting program: /home/jaxigt/Downloads/deadface_re01.bin 
What is the best and sp00kiest breakfast cereal?
Please enter the passphrase: 123

Breakpoint 1, 0x0000555555555153 in main ()
LEGEND: STACK | HEAP | CODE | DATA | RWX | RODATA
───────────────────────────────────────────────────────────────────────[ REGISTERS ]────────────────────────────────────────────────────────────────────────
 RAX  0x68632d746e753063 ('c0unt-ch')
 RBX  0x7fffffffd7f0 ◂— 0x34000333231 /* '123' */
 RCX  0x0
 RDX  0x0
 RDI  0x7fffffffd290 ◂— 0x0
 RSI  0xa
 R8   0x73
 R9   0x7ffff7f7ca60 (main_arena+96) —▸ 0x555555559ab0 ◂— 0x0
 R10  0x77
 R11  0x0
 R12  0x5555555551b0 (_start) ◂— endbr64 
 R13  0x0
 R14  0x0
 R15  0x0
 RBP  0x0
 RSP  0x7fffffffd7d0 ◂— 'flag{c0unt-ch0cula-cereal-FTW}'
 RIP  0x555555555153 (main+147) ◂— cmp    qword ptr [rsp + 0x20], rax
─────────────────────────────────────────────────────────────────────────[ DISASM ]─────────────────────────────────────────────────────────────────────────
 ► 0x555555555153 <main+147>    cmp    qword ptr [rsp + 0x20], rax
   0x555555555158 <main+152>    je     main+196 <main+196>
 
   0x55555555515a <main+154>    lea    rdi, [rip + 0xeff]
   0x555555555161 <main+161>    call   puts@plt <puts@plt>
 
   0x555555555166 <main+166>    mov    rax, qword ptr [rsp + 0x228]
   0x55555555516e <main+174>    xor    rax, qword ptr fs:[0x28]
   0x555555555177 <main+183>    jne    main+223 <main+223>
 
   0x555555555179 <main+185>    add    rsp, 0x230
   0x555555555180 <main+192>    xor    eax, eax
   0x555555555182 <main+194>    pop    rbx
   0x555555555183 <main+195>    ret    
─────────────────────────────────────────────────────────────────────────[ STACK ]──────────────────────────────────────────────────────────────────────────
00:0000│ rsp 0x7fffffffd7d0 ◂— 'flag{c0unt-ch0cula-cereal-FTW}'
01:0008│     0x7fffffffd7d8 ◂— 'nt-ch0cula-cereal-FTW}'
02:0010│     0x7fffffffd7e0 ◂— 'la-cereal-FTW}'
03:0018│     0x7fffffffd7e8 ◂— 0x7d5754462d6c /* 'l-FTW}' */
04:0020│ rbx 0x7fffffffd7f0 ◂— 0x34000333231 /* '123' */
05:0028│     0x7fffffffd7f8 ◂— 0x34000000340
... ↓        2 skipped
───────────────────────────────────────────────────────────────────────[ BACKTRACE ]────────────────────────────────────────────────────────────────────────
 ► f 0   0x555555555153 main+147
   f 1   0x7ffff7de3b25 __libc_start_main+213
   f 2   0x5555555551de _start+46
────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────────
pwndbg> 
```

note the line showing the value in the top of the stack when we hit our break point..

```assembly
00:0000│ rsp 0x7fffffffd7d0 ◂— 'flag{c0unt-ch0cula-cereal-FTW}'
```

## flag{c0unt-ch0cula-cereal-FTW}

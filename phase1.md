# Phase 1

This is definitely the easiest phase. You could easily determine the answer by looking at the output of `strings bomb > strings.txt`, and seeing which
string sticks out like a sore thumb.

```console
knowlel@scofield:~/project2$ gdb bomb
GNU gdb (Ubuntu 8.1-0ubuntu3.2) 8.1.0.20180409-git
Copyright (C) 2018 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "x86_64-linux-gnu".
Type "show configuration" for configuration details.
For bug reporting instructions, please see:
<http://www.gnu.org/software/gdb/bugs/>.
Find the GDB manual and other documentation resources online at:
<http://www.gnu.org/software/gdb/documentation/>.
For help, type "help".
Type "apropos word" to search for commands related to "word"...
Reading symbols from bomb...done.
(gdb) break explode_bomb
Breakpoint 1 at 0x1a78
(gdb) break phase_1
Breakpoint 2 at 0x1264
```
*Load up the bomb file into gdp and set breakpoints for explode_bomb and phase_1*

```console
(gdb) run
Starting program: /home/knowlel/project2/bomb 
Welcome to my fiendish little bomb. You have 6 phases with
which to blow yourself up. Have a nice day!
Hello

Breakpoint 2, 0x0000555555555264 in phase_1 ()
(gdb) disas
Dump of assembler code for function phase_1:
=> 0x0000555555555264 <+0>:     sub    $0x8,%rsp
   0x0000555555555268 <+4>:     lea    0x1841(%rip),%rsi        # 0x555555556ab0
   0x000055555555526f <+11>:    callq  0x555555555774 <strings_not_equal>
   0x0000555555555274 <+16>:    test   %eax,%eax
   0x0000555555555276 <+18>:    jne    0x55555555527d <phase_1+25>
   0x0000555555555278 <+20>:    add    $0x8,%rsp
   0x000055555555527c <+24>:    retq   
   0x000055555555527d <+25>:    callq  0x555555555a78 <explode_bomb>
   0x0000555555555282 <+30>:    jmp    0x555555555278 <phase_1+20>
End of assembler dump.
(gdb)
```
*Run the bomb, enter in something, and lets disassemble the phase_1 method.

Immediately, the address `0x555555556ab0` sticks out, so lets check out what's there.

```console
(gdb) x/s 0x555555556ab0
0x555555556ab0: "You can Russia from land here in Alaska."
(gdb) 
```

[WIP]

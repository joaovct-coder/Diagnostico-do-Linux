# 05 — Diretório /proc

## Objetivo
Consultar informações disponibilizadas pelo kernel sobre o processo.

## Comandos utilizados
Substitua `PID` pelo PID válido do processo escolhido:
```bash
cat /proc/PID/status
cat /proc/PID/stat
cat /proc/PID/io
cat /proc/PID/cmdline | tr '\0' ' '
cat /proc/PID/limits
```
cat /proc/17839/status

Texto do slide:

Passo 4 — Consultar os detalhes do processo Agora execute: cat /proc/17839/status Esse arquivo apresenta informações como estado, PID, PPID, memória e threads.

Terminal:

xubuntu@xubuntu:~$ cat /proc/17839/status
Name:   Isolated Web Co
Umask:  0002
State:  S (sleeping)
Tgid:   17839
Ngid:   0
Pid:    17839
PPid:   10420
TracerPid:      0
Uid:    1000    1000    1000    1000
Gid:    1000    1000    1000    1000
FDSize: 512
Groups: 4 24 27 30 46 100 109 115 1000
NStgid: 17839
NSpid:  17839
NSpgid: 2846
NSsid:  2846
Kthread:        0
VmPeak: 36532856 kB
VmSize:  3058268 kB
VmLck:         0 kB
cat /proc/17839/stat

Texto do slide: /proc/PID/stat — Dados numéricos sobre estado e uso do processo.

Terminal:

xubuntu@xubuntu:~$ cat /proc/17839/stat
17839 (Isolated Web Co) S 10420 2846 2846 0 -1 4194624 1368800 0 4 0 18799 11371 0 0 20 0 26 0 365420 3136942080 118562 18446744073709551615 110844119778928 110844120433920 140723453764544 0 0 0 0 69634 1082134264 0 0 0 17 3 0 0 0 0 0 110844120448056 110844120448560 110844830859264 140723453768081 140723453768413 140723453768413 140723453775821 0
cat /proc/17446/limits

Terminal:

xunbuntotest@xubuntohost:~$ cat /proc/17446/limits
Limit                     Soft Limit           Hard Limit           Units
Max cpu time              unlimited            unlimited            seconds
Max file size             unlimited            unlimited            bytes
Max data size             unlimited            unlimited            bytes
Max stack size            8388608              unlimited            bytes
Max core file size        0                    unlimited            bytes
Max resident set          unlimited            unlimited            bytes
Max processes             27265                27265                processes
Max open files            65536                524288               files
Max locked memory         8388608              8388608              bytes
Max address space         unlimited            unlimited            bytes
Max file locks            unlimited            unlimited            locks
Max pending signals       27265                27265                signals
Max msgqueue size         819200               819200               bytes
Max nice priority         0                    0
Max realtime priority     0                    0
Max realtime timeout      50000                200000               us

# 04 — Threads

obs: tive que usar outra pagina

## Objetivo
Verificar as threads associadas ao processo.

Comando utilizado
bash
ps -T -p 4175
-T: lista as threads do processo, uma por linha.
-p 4175: seleciona o processo analisado, o Isolated Web Co.

Na primeira tentativa o comando foi digitado sem espaço (ps-T) e o terminal respondeu command not found. Com o espaço (ps -T), funcionou.

Transcrição do print
xunbuntotest@xubuntohost:~$ ps-T -p 4175
ps-T: command not found
xunbuntotest@xubuntohost:~$ ps -T -p 4175
    PID    SPID TTY          TIME CMD
   4175    4175 ?        00:00:42 Isolated Web Co
   4175    4181 ?        00:00:00 AsyncSi~lThread
   4175    4183 ?        00:00:03 IPC I/O Child
   4175    4191 ?        00:00:00 Socket Thread
   4175    4192 ?        00:00:00 HTML5 Parser
   4175    4194 ?        00:00:00 StyleThread#1
   4175    4195 ?        00:00:00 StyleThread#2
   4175    4197 ?        00:00:00 JS Watchdog
   4175    4199 ?        00:00:00 RemVidChild
   4175    4206 ?        00:00:00 ImageIO
   4175    4207 ?        00:00:04 Timer
   4175    4212 ?        00:00:00 ImageBridgeChld
   4175    4213 ?        00:00:00 RemoteLzyStream
   4175    4214 ?        00:00:00 ProcessHangMon
   4175    4215 ?        00:00:00 ProfilerChild
   4175    4216 ?        00:00:03 TaskCon~ller #0
   4175    4217 ?        00:00:01 TaskCon~ller #1
   4175    4218 ?        00:00:00 TaskCon~ller #2
   4175    4219 ?        00:00:00 TaskCon~ller #3
   4175    4308 ?        00:00:00 Worker Launcher
   4175    7701 ?        00:00:00 AudioIP~ent RPC
   4175    7703 ?        00:00:00 AudioIP~allback
   4175    8059 ?        00:00:00 Backgro~Pool #3
   4175   11151 ?        00:00:00 StreamT~ns #172
xunbuntotest@xubuntohost:~$
Diagnóstico

Estrutura: o PID 4175 é o do processo, e é igual em todas as linhas. A coluna SPID é o ID de cada thread, e a primeira linha (SPID 4175) é a thread principal. O processo tem 24 threads nesse momento.

Tempo de CPU (TIME):

A thread principal acumulou 42 s, a maior parte do tempo total do processo.
Timer acumulou 4 s, IPC I/O Child e TaskCon~ller #0 3 s cada, e TaskCon~ller #1 1 s.
As demais estão em 0 s, ou seja, ficaram praticamente ociosas.

Comparação com o pstree: os nomes e os TIDs coincidem com a árvore do print anterior, que tinha 23 threads. A diferença é a thread StreamT~ns #172 (SPID 11151), que só aparece aqui. O TID dela é bem maior que os das demais, o que sugere que foi criada mais tarde, mas o print não prova isso.

Outras observações:

Todas as linhas mostram ? na coluna TTY, ou seja, as threads não têm terminal controlador, o que é normal para o processo de um navegador gráfico.
O nome StreamT~ns #172 está abreviado pelo próprio ps.

Conclusão: o ps -T confirma que o processo 4175 é multithread, com 24 threads, e o pstree mostra a mesma estrutura. O consumo de CPU ficou concentrado na thread principal.

# 02 — Árvore de processos obs: Usado em outra pagina do firefox

obs: tive que usar outra pagina do firefox

## Objetivo
Mostrar a relação entre processos e seus processos pais.

Comando utilizado
bash
pstree -p -a -t 4175
-p: mostra o PID (ou TID) de cada item.
-a: mostra os argumentos da linha de comando.
-t: mostra os nomes completos das threads, quando diferem do nome do processo.
4175: processo analisado, o Isolated Web Co.
Transcrição do print
xunbuntotest@xubuntohost:~$ pstree -p -a -t 4175
Isolated Web Co,4175
  ├─{AsyncSi~lThread},4181
  ├─{AudioIP~allback},7703
  ├─{AudioIP~ent RPC},7701
  ├─{Backgro~Pool #3},8059
  ├─{HTML5 Parser},4192
  ├─{IPC I/O Child},4183
  ├─{ImageBridgeChld},4212
  ├─{ImageIO},4206
  ├─{JS Watchdog},4197
  ├─{ProcessHangMon},4214
  ├─{ProfilerChild},4215
  ├─{RemVidChild},4199
  ├─{RemoteLzyStream},4213
  ├─{Socket Thread},4191
  ├─{StyleThread#1},4194
  ├─{StyleThread#2},4195
  ├─{TaskCon~ller #0},4216
  ├─{TaskCon~ller #1},4217
  ├─{TaskCon~ller #2},4218
  ├─{TaskCon~ller #3},4219
  ├─{Timer},4207
  └─{Worker Launcher},4308

Os nomes com ~ aparecem abreviados pelo próprio pstree.

Diagnóstico

Processo: o 4175 é o Isolated Web Co, um processo de conteúdo do Firefox, e é multithread.

Quantidade de threads: a árvore lista 22 threads filhas, mais a thread principal, num total de 23. Esse número muda com o uso do navegador, e o ps -p 4175 -o pid,nlwp,comm confirma o valor naquele momento.

Grupo	Threads	Função provável
Renderização e estilo	StyleThread#1, StyleThread#2, HTML5 Parser, ImageBridgeChld, ImageIO, RemVidChild	Processar a página, o CSS, as imagens e o vídeo
Comunicação	IPC I/O Child, Socket Thread, RemoteLzyStream	Trocar dados com o processo principal e com a rede
Áudio	AudioIP~allback, AudioIP~ent RPC	Reprodução de áudio
Tarefas	TaskCon~ller #0 a #3, Backgro~Pool #3, Worker Launcher, AsyncSi~lThread	Executar tarefas em segundo plano
Monitoramento	JS Watchdog, ProcessHangMon, ProfilerChild, Timer	Vigiar o JavaScript e travamentos, perfilar e controlar tempo

Observação: os TIDs das threads de áudio (7701 e 7703), da Backgro~Pool #3 (8059) e da Worker Launcher (4308) são bem maiores que os das demais (4181 a 4219). Isso sugere que foram criadas depois, durante o uso da página, mas a captura não prova isso.

Conclusão: o processo 4175 tem uma estrutura típica de um processo de conteúdo do Firefox, com várias threads para renderização, comunicação, áudio, tarefas e monitoramento.

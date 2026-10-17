# 01 — PID e PPID

## Objetivo
Identificar o processo analisado e seu processo pai.

## Comandos utilizados
```bash
pgrep -a firefox
ps -o pid,ppid,stat,pri,ni,%cpu,%mem,cmd -p PID
```

## Evidência
Adicione aqui a captura real do comando e da saída, por exemplo `01-pid-ppid.png`.

## Resultado observado
- PID:
- PPID:
- Nome/comando:
- Estado (`STAT`):

## Interpretação
Explique o que os valores mostram e qual processo iniciou o processo analisado.

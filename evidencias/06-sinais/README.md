# Evidência — Sinais SIGSTOP, SIGCONT, SIGTERM

Ambiente: `xunbuntotest@xubuntohost`
Processo alvo: PID 11537 (`Isolated Web Co`, processo de conteúdo do Firefox)

## SIGSTOP

```bash
kill -STOP 11537
ps -p 11537 -o pid,stat,comm
```
```
    PID STAT COMMAND
  11537 Tl   Isolated Web Co
```
Estado passou de `Sl` para `Tl` (stopped).

## SIGCONT

```bash
kill -CONT 11537
ps -p 11537 -o pid,stat,comm
```
```
    PID STAT COMMAND
  11537 Sl   Isolated Web Co
```
Estado voltou de `Tl` para `Sl` (sleeping) — processo retomado.

## SIGTERM

Estado do processo antes do sinal:

```bash
ps -p 11537 -o pid,ppid,stat,ni,%cpu,%mem,comm
```
```
    PID    PPID STAT  NI %CPU %MEM COMMAND
  11537   11113 Sl     0  1.4  4.3 Isolated Web Co
```

Envio do sinal:

```bash
kill -TERM 11537
```

Verificação:

```bash
ps -p 11537
```
```
    PID TTY          TIME CMD
(sem saída — processo encerrado)
```

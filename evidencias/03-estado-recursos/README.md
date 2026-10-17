# 03 — Estado e recursos

## Objetivo
Registrar estado, CPU, memória e prioridade do processo.

## Comandos sugeridos
```bash
ps -p PID -o pid,ppid,stat,ni,pri,%cpu,%mem,nlwp,comm
top -p PID
```

# Evidência — Estado, CPU, memória, prioridade e nice

Processo analisado: PID 11537 (`Isolated Web Co`, processo de conteúdo do Firefox)

## Estado do processo

| Momento | STAT | Significado |
|---|---|---|
| Em repouso | `Sl` | S = sleeping; l = multithreaded |
| Após `kill -STOP` | `Tl` | T = stopped (parado por sinal); l = multithreaded |
| Após `kill -CONT` | `Sl` | Retornou ao estado de espera |
| Após `kill -TERM` | (sem linha de processo) | Só o cabeçalho foi exibido |

```bash
kill -STOP 11537
ps -p 11537 -o pid,stat,comm
```
```
    PID STAT COMMAND
  11537 Tl   Isolated Web Co
```

```bash
kill -TERM 11537
ps -p 11537 -o pid,stat,comm
```
```
    PID STAT COMMAND
```

## CPU e memória

**Momento 1 (repouso):**
```bash
ps -p 11537 -o pid,ppid,stat,ni,%cpu,%mem,comm
```
```
    PID    PPID STAT  NI %CPU %MEM COMMAND
  11537   11113 Sl     0  1.4  4.3 Isolated Web Co
```

**Momento 2 (sob carga):**
```
[PREENCHER] — abrir várias abas / tocar vídeo e capturar novamente:
ps -p 11537 -o pid,%cpu,%mem,rss
```

## Prioridade e nice

Valor de nice antes de qualquer alteração: `NI 0` (ver captura acima).

```
[PREENCHER] — PRI antes, saída do renice e PRI/NI depois (não há capturas)
```

## Interpretação

- **PID 11537:** processo analisado.
- **T:** o processo está parado (*stopped*), normalmente devido a um sinal como SIGSTOP.
- **L (minúsculo `l` no `ps`):** indica que o processo é multithread.
- **Isolated Web Co:** nome do processo de conteúdo do Firefox.

O estado `Tl` confirma que o processo está parado e possui múltiplas threads. O estado `S` em repouso é
típico de processos interativos como o navegador, que passam a maior parte do tempo aguardando eventos
(entrada, rede, renderização). Em repouso, o consumo de CPU é baixo (1,4 %) e o de memória é de 4,3 %.

Após o `kill -TERM`, só o cabeçalho do `ps` apareceu, ou seja, o sistema não encontrou um processo
ativo com esse PID. Isso, junto com a tela de falha da aba do Firefox, é compatível com o encerramento
do processo que atendia à página. Entretanto, o resultado isolado não prova que o SIGTERM foi a única
causa.

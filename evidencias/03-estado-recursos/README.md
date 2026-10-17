# 03 — Estado e recursos

## Objetivo
Registrar estado, CPU, memória e prioridade do processo.

## Comandos sugeridos
```bash
ps -p PID -o pid,ppid,stat,ni,pri,%cpu,%mem,nlwp,comm
top -p PID
```

## Evidências
Adicione capturas de pelo menos dois momentos, se disponíveis:
- `01-recursos-momento1.png`
- `02-recursos-momento2.png`

## Resultados observados
Registre os valores reais de `STAT`, `NI`, `PRI`, `%CPU`, `%MEM` e `NLWP`.

## Interpretação
Compare os momentos e explique as diferenças. CPU e memória variam com o uso do sistema.

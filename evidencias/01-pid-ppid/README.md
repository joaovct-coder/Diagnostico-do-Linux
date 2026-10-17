# Evidência — PID e PPID

```bash
ps -p 17839 -o pid,ppid,stat,ni,%cpu,%mem,nlwp,comm
```
```
    PID    PPID STAT  NI %CPU %MEM NLWP COMMAND
  17839   10420 Sl     0  1.0  5.9   24 Isolated Web Co
```

## Interpretação

O PID `17839` identifica unicamente o processo `Isolated Web Co` (processo do Firefox) no sistema.
O PPID `10420` é o PID do processo pai, aquele que criou o processo. Como o PPID é diferente de `1`,
o processo continua ligado ao seu pai original e não foi reatribuído ao `init`/`systemd`.

Demais campos da consulta:

- **STAT `Sl`:** dormindo (`S`), com múltiplas threads (`l`).
- **NI `0`:** prioridade de execução (nice) padrão.
- **%CPU `1.0` e %MEM `5.9`:** uso aproximado de processador e de memória no momento da consulta.
- **NLWP `24`:** quantidade de threads do processo.

Conclusão parcial: o processo 17839 utiliza aproximadamente 1,0 % de CPU, 5,9 % da memória e possui
24 threads no momento da consulta. Esses valores podem mudar com o uso do navegador.

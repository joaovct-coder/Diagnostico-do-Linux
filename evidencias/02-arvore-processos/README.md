# 02 — Árvore de processos

## Objetivo
Mostrar a relação entre processos e seus processos pais.

## Comando utilizado
```bash
pstree -p
```

## Evidência
Comando:
pstree -p 4175

Resultado observado:
Isolated Web Co(4175)─┬─{Isolated Web Co}(4181)
                      ├─{Isolated Web Co}(4183)
                      ├─{Isolated Web Co}(4191)
                      ├─{Isolated Web Co}(4192)
                      ├─{Isolated Web Co}(4194)
                      ├─{Isolated Web Co}(4195)
                      ├─{Isolated Web Co}(4197)
                      ├─{Isolated Web Co}(4199)
                      ├─{Isolated Web Co}(4206)
                      ├─{Isolated Web Co}(4207)
                      ├─{Isolated Web Co}(4212)
                      ├─{Isolated Web Co}(4213)
                      ├─{Isolated Web Co}(4214)
                      ├─{Isolated Web Co}(4215)
                      ├─{Isolated Web Co}(4216)
                      ├─{Isolated Web Co}(4217)
                      ├─{Isolated Web Co}(4218)
                      ├─{Isolated Web Co}(4219)
                      ├─{Isolated Web Co}(4308)
                      ├─{Isolated Web Co}(4386)
                      └─{Isolated Web Co}(5998)

Interpretação:
O pstree representa o processo 4175 e as threads associadas como ramificações.
O TID 5998 apareceu nessa consulta, mas não na listagem anterior, o que é
compatível com a natureza dinâmica das threads de um processo em execução.

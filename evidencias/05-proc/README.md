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

## Evidências
Adicione capturas legíveis dos arquivos consultados, por exemplo:
- `01-status.png`
- `02-stat.png`
- `03-io.png`
- `04-cmdline.png`
- `05-limits.png`

## Resultados e interpretação
Explique os campos relevantes de cada arquivo. Registre apenas os valores que aparecem nas suas próprias capturas. Um PID pode deixar de existir após o encerramento ou reinício do processo.

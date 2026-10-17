# 06 — Sinais de processo

## Objetivo
Documentar pausa, retomada e solicitação de encerramento de um processo de teste.

## Comandos
Use somente um processo de teste que você tenha escolhido e confira o PID imediatamente antes de agir:
```bash
ps -p PID -o pid,ppid,stat,comm
kill -STOP PID
ps -p PID -o pid,stat,comm
kill -CONT PID
ps -p PID -o pid,stat,comm
kill -TERM PID
ps -p PID -o pid,stat,comm
```

## Evidências
Adicione capturas reais de:
- estado antes do sinal;
- estado após `SIGSTOP` (normalmente inclui `T`);
- estado após `SIGCONT`;
- resultado após `SIGTERM` (o processo pode já não existir).

## Interpretação
Explique o que aconteceu em cada etapa. O `SIGTERM` solicita o encerramento; documente qualquer falha de aba ou efeito observado sem afirmar causalidade que as evidências não comprovem.

# Diagnostico-do-Linux
Esse repositório pra um trabalho avaliativo de sistemas operacionais (Faculdade Serra Dourada)
 Trabalho 1 — Diagnóstico do Linux

Disciplina: Sistemas Operacionais — ADS

Faculdade: Serra Dourada

Professor: Guibson Krause

Aluno(s): Joao Victor Freire
Processo analisado: Firefox (navegador)

1. Descrição da aplicação e justificativa
O processo escolhido foi Firefox, instalado via Snap. Firefox é um navegador de código aberto que a maioria das pessoas usa. A escolha se justifica porque:

Firefox é um processo de usuário que pode ser manipulado com segurança; ele não é um serviço crítico do sistema.

Firefox pode ser interrompido, retomado e encerrado sem causar dano ao sistema operacional.

Firefox tem uma estrutura rica para o diagnóstico: ele cria vários processos filhos (modelo multiprocesso) e cada processo tem várias threads. Isso permite observar bem os conceitos de hierarquia, threads e /proc.

2. Ambiente utilizado
| Item | Detalhe |

|------|---------|

| Distribuição | Ubuntu |

| Máquina | VM (VirtualBox) — usuário vboxuser |

| Instalação do Firefox | Pacote Snap (/snap/firefox/6966/...) |

3. Como executar a aplicação analisada
firefox &
Firefox foi iniciado normalmente pela interface gráfica. Quando o processo inicial termina, o Firefox é “adotado” pelo init/systemd (PID 1). Por isso o PPID observado é 1.

4. Comandos utilizados
Lista completa e comentada em comandos/comandos-utilizados.md.

pgrep -a firefox

ps -o pid,ppid,stat,pri,ni,%cpu,%mem,cmd -p 24287

pstree -p 24287

ps -L -p 24287

cat /proc/24287/status

cat /proc/24287/stat

cat /proc/24287/limits

kill -STOP 24287

kill -CONT 24287

renice 5 -p 24287

kill -TERM 24287

ps -p 24287

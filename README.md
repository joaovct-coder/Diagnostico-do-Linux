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

| Distribuição | Ubuntu |

| Máquina | VM (VirtualBox) — usuário vboxuser |

| Instalação do Firefox |

Conclusão

Para a realização deste trabalho, foram utilizados o Oracle VM VirtualBox, para criar e executar a máquina virtual, o sistema operacional Xubuntu Linux, para realizar os testes, e o navegador Mozilla Firefox, utilizado como aplicação para analisar o comportamento dos processos.

A finalidade do trabalho foi compreender, na prática, como o Linux gerencia seus processos e threads. Foram identificados o PID e o PPID dos processos, analisadas as informações disponíveis no diretório /proc e observadas as threads associadas ao Firefox. A análise de threads permitiu verificar que um processo pode conter várias tarefas de execução, responsáveis por diferentes atividades da aplicação, e que sua quantidade pode variar durante o funcionamento do programa.

Também foram realizados testes com os sinais SIGSTOP, SIGCONT e SIGTERM, para observar, respectivamente, a suspensão, a retomada e a solicitação de encerramento de um processo.

Além disso, foi utilizado o comando nice, que permite iniciar um processo com uma prioridade de execução ajustada. Também foi estudado o comando renice, que permite modificar a prioridade de um processo que já está em execução. No Linux, valores de nice maiores representam menor prioridade de agendamento, enquanto valores menores representam maior prioridade, respeitadas as permissões do usuário.

Conclui-se que a atividade contribuiu para compreender o funcionamento do gerenciamento de processos, threads, sinais e prioridades no Linux, relacionando os conceitos teóricos de Sistemas Operacionais com testes práticos realizados no Xubuntu.

# _**Sistemas Operacionais Modernos**_
## **_Baseado no livro Sistemas Operacionais Modernos de ANDREW S.TANENBAUM e HERBERT BOS_**

<br>
<br>

# Prefácio

## Tópicos importantes
- O sistema operacional cuja função é fornecer aos programas
do usuário um modelo do computador melhor, mais simples e mais limpo, assim como lidar com o gerenciamento de todos os recursos mencionados (um ou mais processadores, alguma memória principal, discos, impressoras, um teclado, um mouse, um monitor, interfaces de rede e vários outros dispositivos de
entrada e saída).
- O programa com o qual os usuários interagem, normalmente chamado de **shell** (ou interpretador de comandos) quando ele é baseado em texto e de **GUI (Graphical User Interface)** quando ele usa ícones
- O sistema operacional, a peça mais fundamental de software, opera em modo núcleo (também chamado modo supervisor). Nesse modo ele tem acesso completo a todo o hardware e pode executar qualquer instrução que a máquina for capaz de executar.

<br>

# **1.1 - O que é um sistema operacional?**
- É difícil dizer com absoluta precisão sua definição. Parte do problema é que os sistemas operacionais realizam duas funções essencialmente não relacionadas: fornecer a programadores de aplicativos (e programas aplicativos, claro) um conjunto de recursos abstratos limpo em vez de recursos confusos de hardware, e gerenciar esses recursos de hardware.Dependendo de quem fala, você poderá ouvir mais a respeito de uma função do que de outra (máquina estendida e gerenciador de recursos).

## 1.1.1 - O Sistema Operacional como Máquina Estendida
- Máquina virtual ou estendida é uma abstração criada pelo S.O. que apresenta ao usuário uma máquina mais simples e com as mesmas funções da máquina real. O S.O em nível de hardware é feio o. Processadores reais, memórias, discos e outros dispositivos são muito complicados e apresentam interfaces difíceis, desajeitadas, idiossincráticas e inconsistentes para as pessoas que têm de escrever softwares para elas utilizarem. Portanto, daí vem a necessidade de ter uma máquina mais simples para o usuário.

## 1.1.2 - O Sistema Operacional como Gerenciador de Recursos
- O conceito de um sistema operacional como fundamentalmente fornecendo abstrações para programas aplicativos é uma visão top-down (abstração de cima para baixo). Uma visão alternativa, bottom-up (abstração de baixo para cima), sustenta que o sistema operacional está ali para gerenciar todas as partes de um sistema complexo. Computadores modernos consistem de processadores, memórias, temporizadores, discos, dispositivos apontadores do tipo mouse, interfaces de rede, impressoras e uma ampla gama de outros dispositivos. Na visão bottom-up, a função do sistema operacional é fornecer uma alocação ordenada e controlada dos processadores, memórias e dispositivos de E/S entre os vários programas competindo por eles. 
- O gerenciamento de recursos inclui a **multiplexação (compartilhamento)** de recursos de duas maneiras diferentes: no **tempo e no espaço.**
- **Tempo:** Quando um recurso é multiplexado no tempo, diferentes programas ou usuários se revezam usando-o. Primeiro, um deles usa orecurso, então outro e assim por diante. Por exemplo,com apenas uma CPU e múltiplos programas querendo ser executados nela, o sistema operacional primeiro aloca a CPU para um programa, então, após ele ter sido executado por tempo suficiente, outro programa passa a fazer uso da CPU, então outro, e finalmente o primeiro de novo. Determinar como o recurso é multiplexado no tempo — quem vai em seguida e por quanto tempo — é a tarefa do sistema operacional. Outro exemplo da multiplexação no tempo é o compartilhamento da impressora. Quando múltiplas saídas de impressão estão na fila para serem impressas em uma única impressora, uma decisão tem de ser tomada sobre qual deve ser impressa em seguida. 
- **Espaço:**: O outro tipo é a multiplexação de espaço. Em vez de os clientes se revezarem, cada um tem direito a uma parte do recurso. Por exemplo, a memória principal é normalmente dividida entre vários programas sendo executados, de modo que cada um pode ser residente ao mesmo tempo (por exemplo, a fim de se revezar usando a CPU). Presumindo que há memória suficiente para manter múltiplos programas, é mais eficiente mantervários programas na memória ao mesmo tempo do que dar a um deles toda ela, especialmente se o programa precisa apenas de uma pequena fração do total. É claro, isso gera questões de justiça, proteção e assim por diante, e cabe ao sistema operacional solucioná-las. Outro recurso que é multiplexado no espaço é o disco. Em muitos sistemas um único disco pode conter arquivos de muitos usuários ao mesmo tempo. Alocar espaço de disco e controlar quem está usando quais blocos do disco é uma tarefa típica do sistema operacional. 

<br>

# **1.2 - História dos Sistemas Operacionais**
- Esse tópico será pulado pois não há cobrança para a avaliação, porém se alguém por ventura quiser lê-lo depois, está no livro contido no repositório

<br>

# **1.3 - Revisão de hardware de computadores**

## 1.3.1 - Processadores






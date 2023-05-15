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
- O “cérebro” do computador é a CPU. Ela busca instruções da memória e as executa. O ciclo básico de toda CPU é buscar a primeira instrução da memória, decodificá-la para determinar o seu tipo e operandos, executá- -la, e então buscar, decodificar e executar as instruções subsequentes. O ciclo é repetido até o programa terminar. É dessa maneira que os programas são executados
- Como o tempo para acessar a memória para buscar uma instrução ou palavra dos operandos é muito maior do que o tempo para executar uma instrução, todas as CPUs têm alguns  registradores internos para armazenamento de variáveis e resultados temporários. Desse modo, o conjunto de instruções geralmente contém instruções para carregar uma palavra da memória para um registrador e armazenar uma palavra de um registrador para a memória.
- **Multithreading ou Hyperthreading:**  Para uma primeira aproximação, o que ela faz é permitir que a CPU mantenha o estado de dois threads diferentes e então faça o chaveamento entre um e outro em uma escala de tempo de nanossegundos.

## 1.3.2 - Memória
- O segundo principal componente em qualquer computador é a memória. Idealmente, uma memória deve ser rápida ao extremo (mais rápida do que executar uma instrução, de maneira que a CPU não seja atrasada pela memória), abundantemente grande e muito barata. Nenhuma tecnologia atual satisfaz todas essas metas, assim uma abordagem diferente é tomada. 

## 1.3.3 - Discos
- Em seguida na hierarquia está o disco magnético (disco rígido). O armazenamento de disco é duas ordens de magnitude mais barato, por bit, que o da RAM e frequentemente duas ordens de magnitude maior também. O único problema é que o tempo para acessar aleatoriamente os dados é próximo de três ordens de magnitude mais lento. Isso ocorre porque o disco é um dispositivo mecânico.
- Às vezes você ouvirá as pessoas falando sobre discos que não são discos de maneira alguma, como os SSDs (Solid State Disks — discos em estado sólido). SSDs não têm partes móveis, não contêm placas na forma de discos e armazenam dados na memória (flash). A única maneira pela qual lembram discos é que eles também armazenam uma quantidade grande de dados que não é perdida quando a energia é desligada. 

## 1.3.4 - Dispositivos de E/S
- Dispositivos de entrada e saída são componentes físicos ou virtuais de um sistema computacional que permitem a interação entre o usuário e o sistema operacional, permitindo a entrada de dados para o sistema e a saída de resultados ou informações do sistema. Dispositivos de entrada são utilizados para enviar dados ou comandos para o sistema operacional. Alguns exemplos comuns de dispositivos de entrada são:
    1. Teclado: Permite a entrada de caracteres, comandos e outras informações por meio de teclas.
    1. Mouse: É usado para mover o cursor na tela e realizar seleções ou interações com elementos gráficos.
    1. Scanner: Permite digitalizar documentos e converter informações em formato digital.
    1. Microfone: Usado para capturar sons e entrada de áudio.
    1. Sensores: Dispositivos como sensores de temperatura, acelerômetros, leitores de código de barras, entre outros, podem ser usados como dispositivos de entrada para fornecer dados ao sistema operacional.
- Por outro lado, dispositivos de saída são responsáveis por exibir os resultados, informações ou sinais gerados pelo sistema operacional. Alguns exemplos de dispositivos de saída são:
    1. Monitor ou tela: Exibe informações, gráficos, vídeos e interface do usuário.
    1. Impressora: Gera cópias físicas de documentos ou imagens.
    1. Alto-falantes ou fones de ouvido: Produzem saída de áudio, reproduzindo sons ou música. 
    1. Dispositivos de exibição tátil (touchscreen): Permitem interações diretas com a interface do usuário por meio de toques na tela.
    1. Dispositivos de rede: Permitem a transmissão de dados do sistema para outros dispositivos, como modems, roteadores, placas de rede, etc.
- O sistema operacional é responsável por gerenciar a comunicação entre o software e os dispositivos de entrada e saída. Ele fornece interfaces e drivers necessários para garantir que os dispositivos possam ser utilizados corretamente pelos aplicativos e pelos usuários. Dessa forma, os dispositivos de entrada e saída são essenciais para a interação e o funcionamento dos sistemas operacionais.

## 1.3.5 - Barramentos
- Em sistemas operacionais, os barramentos referem-se a um conjunto de linhas de comunicação físicas ou virtuais que permitem a transferência de dados entre os componentes de hardware do computador. Eles são canais de comunicação que conectam a unidade central de processamento (CPU), a memória, os dispositivos de entrada/saída e outros componentes do sistema. Existem diferentes tipos de barramentos em um sistema computacional, cada um com uma função específica. Aqui estão alguns dos barramentos comumente encontrados:
    1. Barramento do sistema (system bus): É o barramento principal que conecta a CPU à memória e outros dispositivos principais. Ele permite a transferência de dados, endereços e sinais de controle entre esses componentes. O barramento do sistema inclui o barramento de dados (data bus), o barramento de endereço (address bus) e o barramento de controle (control bus).
    1. Barramento de dados (data bus): É usado para a transferência de dados entre a CPU, a memória e os dispositivos de entrada/saída. Ele carrega os bits de dados que são processados pela CPU ou transmitidos entre diferentes componentes.
    1. Barramento de endereço (address bus): É responsável por transportar os endereços de memória que são usados para identificar a localização dos dados ou instruções na memória. Ele permite que a CPU acesse áreas específicas da memória para leitura ou escrita.
    1. Barramento de controle (control bus): Carrega sinais de controle que controlam as operações e a sincronização dos componentes do sistema. Ele inclui sinais como leitura/escrita, interrupção, sinal de relógio, sinais de controle de barramento, entre outros.
- Além desses barramentos principais, existem barramentos especializados que são projetados para conectar dispositivos específicos, como barramentos PCI (Peripheral Component Interconnect) para dispositivos de expansão, barramentos USB (Universal Serial Bus) para conexão de periféricos, barramentos Ethernet para redes de computadores, entre outros.
- Os sistemas operacionais lidam com os barramentos ao controlar a alocação e o gerenciamento de recursos do sistema, permitindo que os componentes de hardware se comuniquem de maneira eficiente e coordenada. Os drivers de dispositivo são responsáveis por fornecer suporte para o acesso aos barramentos específicos e garantir a interoperabilidade entre o sistema operacional e os dispositivos conectados.

<br>

# 1.4 - **O zoológico dos sistemas operacionais**
- Por hora será pulado, pois não é tão urgente assim.

<br>

# 1.5 - **Conceitos de Sistemas Operacionais**

## 1.5.1 - Processos



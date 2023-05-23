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
- **Tempo:** Quando um recurso é multiplexado no tempo, diferentes programas ou usuários se revezam usando-o. Primeiro, um deles usa o recurso, então outro e assim por diante. Por exemplo, com apenas uma CPU e múltiplos programas querendo ser executados nela, o sistema operacional primeiro aloca a CPU para um programa, então, após ele ter sido executado por tempo suficiente, outro programa passa a fazer uso da CPU, então outro, e finalmente o primeiro de novo. Determinar como o recurso é multiplexado no tempo — quem vai em seguida e por quanto tempo — é a tarefa do sistema operacional. Outro exemplo da multiplexação no tempo é o compartilhamento da impressora. Quando múltiplas saídas de impressão estão na fila para serem impressas em uma única impressora, uma decisão tem de ser tomada sobre qual deve ser impressa em seguida. 
- **Espaço:**: O outro tipo é a multiplexação de espaço. Em vez de os clientes se revezarem, cada um tem direito a uma parte do recurso. Por exemplo, a memória principal é normalmente dividida entre vários programas sendo executados, de modo que cada um pode ser residente ao mesmo tempo (por exemplo, a fim de se revezar usando a CPU). Presumindo que há memória suficiente para manter múltiplos programas, é mais eficiente manter vários programas na memória ao mesmo tempo do que dar a um deles toda ela, especialmente se o programa precisa apenas de uma pequena fração do total. É claro, isso gera questões de justiça, proteção e assim por diante, e cabe ao sistema operacional solucioná-las. Outro recurso que é multiplexado no espaço é o disco. Em muitos sistemas um único disco pode conter arquivos de muitos usuários ao mesmo tempo. Alocar espaço de disco e controlar quem está usando quais blocos do disco é uma tarefa típica do sistema operacional. 

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
- Um conceito fundamental em todos os sistemas operacionais é o processo. Um processo é basicamente um programa em execução. Associado a cada processo está o espaço de endereçamento, uma lista de posições de memória que vai de 0 a algum máximo, onde o pro-cesso pode ler e escrever. Um processo é na essência um contêiner que armaze-na todas as informações necessárias para executar um programa.


## 1.5.2 - Espaços de Endereçamento
- Todo  computador  tem  alguma  memória  principal que  ele  usa  para  armazenar  programas  em  execução. Em um sistema operacional muito simples, apenas um programa de cada vez está na memória. Para executar um segundo programa, o primeiro tem de ser removido e o segundo colocado na memória. Sistemas  operacionais  mais  sofisticados  permitem que múltiplos programas estejam na memória ao mes-mo tempo. Para evitar que interfiram entre si (e com o sistema operacional), algum tipo de mecanismo de pro-teção é necessário. Embora esse mecanismo deva estar no hardware, ele é controlado pelo sistema operacional.


## 1.5.3 - Arquivos
- Outro  conceito  fundamental  que  conta  com  o  su-porte  de  virtualmente  todos  os  sistemas  operacionais é o sistema de arquivos. Como já foi observado, uma função importante do sistema operacional é esconder as peculiaridades dos discos e outros dispositivos de E/S e  apresentar  ao  programador  um  modelo  agradável  e claro de arquivos que sejam independentes dos disposi-tivos. Chamadas de sistema são obviamente necessárias para criar, remover, ler e escrever arquivos. Antes que um arquivo possa ser lido, ele deve ser localizado no disco e aberto, e após ter sido lido, deve ser fechado, assim as chamadas de sistema são fornecidas para fazer essas coisas. Para fornecer um lugar para manter os arquivos, a maioria dos sistemas operacionais de PCs tem o conceito de um diretório como uma maneira de agrupar os arquivos. Um estudante, por exemplo, pode ter um diretório para cada curso que ele estiver seguindo (para os programas necessários para aquele curso), outro para o correio eletrônico e ainda um para sua página na web. Chamadas de sistema são então necessárias para criar e remover diretórios. Chamadas também são fornecidas para  colocar  um  arquivo  existente  em  um  diretório  e para remover um arquivo de um diretório. Entradas de diretório podem ser de arquivos ou de outros diretórios. 

## 1.5.4 - Entrada/Saída
- Todos os computadores têm dispositivos físicos para obter entradas e produzir saídas. Afinal, para que servi-ria um computador se os usuários não pudessem dizer a ele o que fazer e não pudessem receber os resultados após ele ter feito o trabalho pedido? Existem muitos ti-pos de dispositivos de entrada e de saída, incluindo te-clados, monitores, impressoras e assim por diante. Cabe ao sistema operacional gerenciá-los. Em consequência, todo sistema operacional tem um subsistema de E/S para gerenciar os dispositivos de E/S. Alguns softwares de E/S são independentes do dispo-sitivo, isto é, aplicam-se igualmente bem a muitos ou a todos dispositivos de E/S. Outras partes dele, como drivers de dispositivo, são específicos a dispositivos de E/S particulares.

## 1.5.5 - Proteção
- Todos os computadores têm dispositivos físicos para obter entradas e produzir saídas. Afinal, para que servi-ria um computador se os usuários não pudessem dizer a ele o que fazer e não pudessem receber os resultados após ele ter feito o trabalho pedido? Existem muitos ti-pos de dispositivos de entrada e de saída, incluindo te-clados, monitores, impressoras e assim por diante. Cabe ao sistema operacional gerenciá-los. Em consequência, todo sistema operacional tem um subsistema de E/S para gerenciar os dispositivos de E/S. Alguns softwares de E/S são independentes do dispo-sitivo, isto é, aplicam-se igualmente bem a muitos ou a todos dispositivos de E/S. Outras partes dele, como drivers de dispositivo, são específicos a dispositivos de E/S particulares.

## 1.5.6 - O interpretador de comandos (shell)
- o sistema operacional é o código que executa as chamadas de sistema. Editores, compiladores, montadores, ligadores (linkers), programas utilitários e interpretado-res de comandos definitivamente não fazem parte do sis-tema operacional, mesmo que sejam importantes e úteis. Correndo o risco de confundir as coisas de certa maneira, nesta seção examinaremos brevemente o interpretador de comandos UNIX, o shell. Embora não faça parte do sistema operacional, ele faz um uso intensivo de muitos aspectos do sistema operacional e serve assim como um bom exemplo de como as chamadas de sistema são usa-das. Ele também é a principal interface entre um usuário sentado no seu terminal e o sistema operacional, a não ser que o usuário esteja usando uma interface de usuário gráfica.

<br>

# 1.6 - **Chamadas ao sistema**

## Conceito inicial
- Em sistemas operacionais, <mark style="background: purple; color: white; font-weight: 500">as chamadas de sistema (também conhecidas como system calls) são interfaces fornecidas pelo sistema operacional que permitem que os programas de aplicação solicitem serviços e recursos do sistema operacional. Elas são a maneira pela qual os programas de usuário interagem com o kernel do sistema operacional.</mark>
- Quando um programa de aplicação precisa executar uma operação que requer acesso privilegiado ou serviços oferecidos pelo sistema operacional, ele faz uma chamada de sistema específica para solicitar essas ações. Essas chamadas podem incluir operações como leitura ou escrita em arquivos, criação de processos, alocação de memória, acesso a dispositivos de entrada e saída, entre outras.
- As chamadas de sistema fornecem uma abstração para os programas de aplicação, permitindo que eles utilizem as funcionalidades do sistema operacional de maneira segura e controlada. Quando uma chamada de sistema é feita, o programa de usuário transfere o controle para o kernel do sistema operacional, que executa a operação solicitada em nome do programa e retorna os resultados apropriados.
- As chamadas de sistema são uma parte fundamental dos sistemas operacionais e desempenham um papel importante na execução de tarefas do sistema, garantindo a segurança e a proteção dos recursos do sistema, bem como a interação entre os programas de usuário e o sistema operacional.
- As principais funções do kernel são:
    1.Tratamento de interrupções e exceções
    1.Criação e eliminação de processos
    1.Sincronização e comunicação entre processos
    1.Escalonamento e controle dos processos
    1.Gerência de memória
    1.Gerência do sistema de arquivos
    1.Gerência de dispositivos de E/S
    1.Suporte a redes locais e distribuídas
    1.Segurança do sistema


## 1.6.1 - Chamadas de sistema para gerenciamento de processos
- As chamadas de sistema para gerenciamento de processos permitem que os programas de aplicação interajam com o sistema operacional para criar, controlar e manipular processos. Essas chamadas de sistema fornecem os meios para criar novos processos, encerrar processos existentes, obter informações sobre processos em execução, sincronizar processos e realizar operações relacionadas ao escalonamento e comunicação entre processos. Abaixo estão algumas das principais chamadas de sistema relacionadas ao gerenciamento de processos:
    1. **Fork:** A chamada de sistema fork é usada para criar um novo processo, que é uma cópia exata do processo pai. O processo filho começa a partir do ponto em que o fork foi chamado, e ambos o processo pai e o processo filho continuam a execução a partir desse ponto, mas com identificadores de processo (PID) diferentes.
    1. **Exec:** As chamadas de sistema exec são usadas para substituir o código de um processo pelo código de outro programa. Elas permitem que um processo inicie a execução de um novo programa, carregando-o na memória e substituindo seu próprio código. Existem várias variantes dessa chamada, como execve, execl, execvp, entre outras.
    1. **Wait:** A chamada de sistema wait é usada para suspender a execução de um processo pai até que um de seus processos filhos termine a execução. Isso permite que o processo pai aguarde a conclusão de um processo filho específico ou qualquer processo filho.
    1. **Exit:** A chamada de sistema exit é usada para terminar a execução de um processo. Quando um processo chama exit, ele é encerrado e todos os recursos associados a ele são liberados pelo sistema operacional.
    1. **Kill:** A chamada de sistema kill é usada para enviar um sinal para um processo específico ou grupo de processos. Os sinais são usados para notificar os processos sobre eventos ou solicitar a execução de ações específicas.
    1. **Scheduling:** As chamadas de sistema relacionadas ao escalonamento de processos permitem que um processo solicite mudanças na prioridade de escalonamento, aguarde por um certo período de tempo ou bloqueie sua execução até que uma condição específica seja atendida.
    - Essas são apenas algumas das chamadas de sistema relacionadas ao gerenciamento de processos. Elas fornecem as ferramentas necessárias para criar, controlar e coordenar a execução de processos em um sistema operacional. Cada sistema operacional pode ter suas próprias chamadas de sistema específicas, mas os conceitos básicos de criação, término, sincronização e comunicação de processos são amplamente utilizados em diferentes sistemas operacionais.


## 1.6.2 Chamadas de sistema para gerenciamento de arquivos
- As chamadas de sistema para gerenciamento de arquivos permitem que os programas de aplicação interajam com o sistema operacional para criar, abrir, ler, gravar, renomear, mover e excluir arquivos. Essas chamadas de sistema fornecem as funcionalidades necessárias para manipular arquivos e diretórios em um sistema de armazenamento. Aqui estão algumas das principais chamadas de sistema relacionadas ao gerenciamento de arquivos:
    1. **Create:** A chamada de sistema create é usada para criar um novo arquivo com um determinado nome. Ela retorna um identificador de arquivo que pode ser usado para operações subsequentes no arquivo.
    1. **Open:** A chamada de sistema open é usada para abrir um arquivo existente. Ela também retorna um identificador de arquivo para permitir operações adicionais no arquivo.
    1. **Read:** A chamada de sistema read é usada para ler uma quantidade específica de dados de um arquivo aberto para um buffer na memória do programa.
    1. **Write:** A chamada de sistema write é usada para escrever uma quantidade específica de dados de um buffer na memória para um arquivo aberto.
    1. **Close:** A chamada de sistema close é usada para fechar um arquivo aberto, liberando recursos associados a ele e indicando que nenhuma outra operação será realizada nele.
    1. **Rename:** A chamada de sistema rename é usada para renomear um arquivo existente, alterando o nome pelo qual ele é conhecido no sistema de arquivos.
    1. **Delete:** A chamada de sistema delete é usada para excluir um arquivo existente do sistema de arquivos.
    1. **Seek:** A chamada de sistema seek é usada para reposicionar o ponteiro de leitura/escrita em um arquivo aberto, permitindo acesso aleatório a diferentes partes do arquivo.
    - Essas são apenas algumas das chamadas de sistema relacionadas ao gerenciamento de arquivos. Elas permitem que os programas de aplicação acessem, criem, modifiquem e excluam arquivos no sistema de armazenamento controlado pelo sistema operacional. Cada sistema operacional pode ter suas próprias chamadas de sistema específicas, mas os conceitos básicos de manipulação de arquivos são amplamente utilizados em diferentes sistemas operacionais.

# 1.6.3 - Chamadas de sistema para gerenciamento de diretórios
- As chamadas de sistema para gerenciamento de diretórios permitem que os programas de aplicação interajam com o sistema operacional para criar, abrir, ler, gravar, renomear, mover e excluir diretórios. Essas chamadas de sistema fornecem as funcionalidades necessárias para manipular a estrutura de diretórios em um sistema de arquivos. Aqui estão algumas das principais chamadas de sistema relacionadas ao gerenciamento de diretórios:
1. **Create Directory:** A chamada de sistema mkdir é usada para criar um novo diretório com um determinado nome dentro de um diretório existente.
1. **Open Directory:** A chamada de sistema opendir é usada para abrir um diretório existente, permitindo a leitura dos arquivos e subdiretórios contidos nele.
1. **Read Directory:** A chamada de sistema readdir é usada para ler o próximo arquivo ou subdiretório em um diretório aberto. Ela retorna informações sobre o arquivo, como nome e tipo.
1. **Write Directory:** Geralmente, os sistemas operacionais não oferecem uma chamada de sistema específica para gravar diretórios, pois a estrutura e organização dos diretórios são gerenciadas automaticamente pelo sistema operacional.
1. **Rename Directory:** A chamada de sistema rename também pode ser usada para renomear diretórios existentes, alterando o nome pelo qual eles são conhecidos no sistema de arquivos.
1. **Delete Directory:** A chamada de sistema rmdir é usada para excluir um diretório existente, desde que esteja vazio, ou seja, não contenha nenhum arquivo ou subdiretório.
- Essas são algumas das chamadas de sistema comumente usadas para o gerenciamento de diretórios. Elas permitem que os programas de aplicação criem, naveguem e manipulem diretórios dentro do sistema de arquivos controlado pelo sistema operacional. É importante observar que as chamadas de sistema podem variar dependendo do sistema operacional específico, mas os conceitos básicos de manipulação de diretórios são amplamente utilizados em diferentes sistemas operacionais.

<br>

# **Estrutura dos Sistemas Operacionais**

## 1.7.1 - Sistemas Monolíticos
- A mais comum, nessa abordagem <mark style="background-color: seagreen; color: white; font-weight: 500"> todo o sistema operacional é executado como um único programa em modo núcleo.</mark>. O sistema operacional é escrito como uma coleção de rotinas , ligadas a um único grande programa binário executável. Nessa técnica, cada procedimento é livre para chamar qualquer outro, se este oferecer alguma computação útil de que o primeiro precisa. Ser capaz de chamar qualquer procedimento que você quer é muito eficiente, mas ter milhares de procedimentos que  podem  chamar  um  ao  outro  sem  restrições  pode também levar a um sistema difícil de lidar e compre-ender. Também, uma quebra em qualquer uma dessas rotinas derrubará todo o sistema operacional.

## 1.7.2 - Sistemas de Camadas



| Camada   |  Função                                     |
| :------: | :------                                     |
| 5        | Operador                                    |    
| 4        | Programas de usuário                        |    
| 3        | Controle de Entrada e Saída                 |    
| 2        | Comunicação operador-processo               |    
| 1        | Gerenciamento de memória                    |    
| 0        | Alocação do processador e multiprogramação  |     

- **Camada 0:** Fornecia os serviços para a multiprogramação básica da CPU. Realizava chaveamento de processos quando temporizadores expiravam ou quando ocorriam interrupções.
- **Camada 1:** Reserva espaço para os processos na memória principal. As camadas acima não precisavam se preocupar com tal tarefa. A camada 1 assegurava que as páginas eram trazidas para MP quando necessário.
- **Camada 2:** Encarregava-se de comunicação entre cada processo e o console de operação.
- **Camada 3:** Encarregava-se do gerenciamento dos dispositivos de E/S, armazenando temporariamente os fluxos de instrução que vinham ou iam para estes dispositivos.
- **Camada 4:** Ficavam os programas do usuário.
- **Camada 5:** Ficava o processo operador do sistema.
- **Vantagens:**
    - A primeira camada pode ser depurada sem qualquer preocupação com o restante do sistema (utiliza apenas o HW básico)
    - Quando a primeira camada é depurada, sua funcionalidade correta pode ser assumida, e assim por diante.
- A principal dificuldade é decidir em qual camada uma determinada funcionalidade estará presente.
- Cada camada acrescenta um custo adicional à chamada de sistema.

# 1.7.3 - Micronúcleo (MicroKernel)
- Sua abordagem é toner o núcleo do SO o mais simples possível
    - No sistema em camadas, muitas camadas entramm no núclo do SO.
- Estrutura o sistema operacional removendo todos os componentes não essenciais ao kernel, implementando-os como programas no nível de sistema e do usuário.
- Existe pouco consenso sobre quais serviços devem permanecer kernel.
    - Fornece uam gerência mínima de processo e memória, além de facilidade de comunicação.
- O objetivo é alcançar alta confiabilidade por meio da divisão do SO em módulos pequenos.
- Somente o micronúcleo é executado em modo kernel.
- Os demais processos são executados em modo usuário, onde um erro pode derrubar somente o processo e não todo o sistema.
- Usado em aplicações de tempo real, aviônica e industrias por exemplo.

## 1.7.4 - Modelo Cliente-Servidor
- O serviço é solicitado pelo cliente envia uma mensagem ao processo servidor.
- O servidor realiza o trabalho e envia a resposta através de outra mensagem.
- O núcleo do SO trata a comunicação entre clientes e servidores.
- A vantagem é a fácil adaptação para sistemas distribuídos.
- Normalmente o que se implementa é uma combinação do sistema de camadas com o modelo cliente-servidor.
- Nestes casos, o núcleo do sistema além de ser responsável pela comunicação entre processos clientes e servidores, passa a incorporar outras funções críticas:
    - Gerência de E/S;
    - Gerência de memória;
    - Escalonamento de processos.

<br>
<br>

# 2 - **Processos e Threads**

## 2.1 - Processos
- Em sistemas operacionais, um processo é uma instância em execução de um programa de computador. Ele representa uma unidade de trabalho independente, com seu próprio espaço de endereçamento, conjunto de registradores e pilha de execução. Um processo é uma entidade dinâmica que pode ser programada e gerenciada pelo sistema operacional.
- Os processos mantém a capacidade de operações concorrentes mesmo quando há apenas uma CPU disponível.
- <mark style="background: darkcyan; color: white; font-weight: 500">Um processo é um programa em execução.</mark>
- *Exemplo:*
    - Fazer um bolo:
        - Receita → Programa
        - Ingredientes → Dados de entrada
        - O cozinheiro → CPU
- Possui 3 elementos básicos: contexto de software, contexto de hardware e espaço de endereçamento.
    - Contexto de SW: Características do processo como: identificação, número máximo de arquivos abertos, privilégios, etc
    - Contexto de HW: Constitui basicamente o conteúdo dos registradores
    - Espaço de endereçamento: É a área de memória pertencente ao processo, onde estarão armazenados as instruções e os dados para a execução.
- O que esperar do SO:
    - Alternar a execução de processos de forma a maximizar a utilização da CPU e fornecer tempo de resposta razoável
    - Alocar recursos a processos
    - Suportar criação de processos pelo usuário
    - Suportar comunicação entre processos
- Para gerenciar processos o SO precisa conhecer onde o processo está localizado e os atributos do processo
 -O SO materializa o processo através do bloco de controle de processo – PCB
 - O PCB de todos os processos ativos residem na memória principal em uma área exclusiva do SO
 - Usado para armazenar informações do processo
- Bloco de Controle do Processo (Process Control Block)
    - Estado do Processo
    - Número do Processo (PID)
    - Contador de Programa (PC)
    - Registradores da CPU
    - Informações de gerenciamento da memória (registradores base e limite, tabelas de páginas ou de segmentos, etc)
    - Informações de status de I/O (lista de arquivos abertos, lista de dispositivos alocados a um processo, etc)
    - Informações de Contabilização (tempo de execução real e de CPU, etc)
    - Informações de escalonamento (prioridade, ponteiros para filas de escalonamento, parâmetros)
- A gerência de processos é realizada por intermédio de chamadas às rotinas do SO, que realizam funções como criação, eliminação, sincronização, etc.
- O SO toma grande cuidado para que processos independentes não afetem, de modo intencional ou por acidente, a correção de comportamento um do outro
    - Vários processos compartilham concorrentemente a CPU e outros recursos de HW de forma transparente
- A troca de um processo por outra é comandada pelo SO → Troca de Contexto
- Sobrecarga associada troca de contexto:
    - Salva contexto do processo
    - Atualiza bloco de controle do processo (PCB)
        - Gravação do novo estado (pronto/bloqueado...)
    - Move o processo (PCB) para a fila apropriada
    - Escolhe novo processo para execução
    - Atualiza PCB do novo processo e dados relativos a MP
    - Restaura contexto do novo processo
- O que faz o SO para criar processos?
    - Constrói estruturas de dados
    - Aloca espaço de endereçamento
- Quando o processo é criado?
    - Início do sistema
    - Requisição do usuário 
    - Submissão de um job (batch)
    - Processo cria outros processos
- Um processo termina devido alguma das seguintes situações:
    - Saída normal (voluntária)
    - Saída por erro (voluntária)
        - Ex. Um compilador termina a execução quando vai compilar um arquivo que não existe
    - Erro fatal (involuntário)
        - Ex. Execução de instrução ilegal, divisão por zero...
    - Cancelamento por outro processo (involuntário)
        - Ex. Comando kill no Linux

## 2.1.2 - Estados dos Processos

- **Novo:** O processo está sendo criado
- **Em execução:** Instruções estão sendo executadas
- **Em espera (ou bloqueado):** aguardando por algum evento (conclusão de I/O ou recebimento de um sinal)
- **Pronto:** esperando para ser atribuído a um processador
- **Terminado:** O processo terminou a sua execução

# 2.1.3 - Estado Suspenso

- Vários processos em execução –necessidadede espaço em MP disponível
-Importante para implementação de memóriavirtual
- O processador é muitomais rápido que E/S: todos os processos podem estar bloqueados 
- Necessidade de novo estado→Suspenso 
    - Imagem do processo sai temporariamente da MP
    - SO seleciona um dos bloqueados para sair de MP
    - É um operaçãode E/S



<br>

# 2.2 - Threads

## Conceito inicial
- Uma thread, também conhecida como uma "thread de execução" ou "encadeamento", é uma sequência de instruções que pode ser executada em paralelo com outras threads dentro de um processo. Em outras palavras, uma thread é uma unidade de execução dentro de um processo que compartilha o mesmo espaço de endereçamento e recursos, mas tem seu próprio estado de execução.
- Aqui estão algumas características importantes das threads:
    
    1.**Execução concorrente:** As threads permitem que várias sequências de instruções sejam executadas em paralelo dentro de um único processo. Cada thread pode executar um conjunto diferente de instruções, operar em dados diferentes e ter seu próprio estado de execução independente.

    1. **Compartilhamento de recursos:** As threads em um processo compartilham o mesmo espaço de endereçamento e recursos do sistema, como memória, arquivos abertos, manipuladores de E/S e outros recursos. Isso permite que as threads acessem e compartilhem informações entre si mais facilmente, sem a necessidade de comunicação explícita.

    1. **Criação e destruição dinâmica:** As threads podem ser criadas e destruídas dinamicamente durante a execução de um programa. Isso permite que o programa adapte a criação de threads de acordo com as necessidades, como a paralelização de tarefas intensivas em computação ou o gerenciamento de eventos assíncronos.

    1. **Escalonamento:** As threads são escalonadas pelo sistema operacional, assim como os processos. O sistema operacional decide a ordem em que as threads recebem tempo de execução na CPU e pode usar algoritmos de escalonamento para equilibrar a carga do sistema e garantir a justiça na alocação de recursos.

    1. **Benefícios de desempenho:** As threads podem melhorar o desempenho e a capacidade de resposta de um programa, permitindo a execução concorrente de tarefas que podem ser paralelizadas. Isso é especialmente útil em sistemas com múltiplos núcleos de CPU, onde várias threads podem ser executadas verdadeiramente em paralelo.

- As threads são usadas para implementar a programação multithread, que é uma abordagem em que várias threads cooperam entre si para realizar tarefas simultâneas e melhorar o desempenho geral do programa. As threads podem ser usadas para dividir tarefas complexas em partes menores, lidar com operações de E/S assíncronas, responder a eventos em tempo real e realizar cálculos paralelos.
- No entanto, é importante observar que as threads também podem introduzir desafios adicionais, como condições de corrida (quando várias threads acessam e modificam os mesmos recursos simultaneamente) e sincronização (garantir a ordem correta de execução e evitar resultados inconsistentes). O desenvolvimento de programas multithread requer considerações cuidadosas para garantir a corretude e a robustez do código.
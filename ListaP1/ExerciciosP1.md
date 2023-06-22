# **_Lista de exercícios para P1_**

<br>

## 1. O que é um sistema Operacional? Quais as suas funções principais?
- Resposta:
    - O sistema operacional é um software, ou conjunto de softwares, cuja função é administrar e gerenciar os recursos de um sistema, desde componentes de hardware e sistemas de arquviso a programas de terceiros, estabelecendo a interface entre computador e usuário.
    - O sistema operacional introduz uma camada de abstração entre o hardware e o usuário, que transforma comandos no mouse, teclado e solicitações do sistema, como gerenciamento de recursos (CPU, memória RAM), em linguagem de máquina, enviando instruções ao processador.
    - Em suma, o sistema operacional, tem as funções básicas de interpretar os comandos do usuário; controlar os periféricos (teclado, vídeo, discos, impressora, mouse, plotter, etc) e organizar arquivos em disco

- Gabarito da professora:
    - <mark style="background: crimson; font-weight: 500; color: white">O SO é um programa que controla a execução de programas aplicativos e age como interface entre as aplicações e hardware. Um sistema operacional possui 3 objetivos principais: Executar os programas do usuário de maneira mais simples, tornar os sistemas computacionais convenientes para o usar e usar os dispositivos de harware de forma eficiente.</mark>
    - <mark style="background: crimson; font-weight: 500; color: white">O SO pode ser visto como Máquina virtual oferecendo os seguintes serviços: Facilidades para desenvolvimento de programas; rotinas para execução de programas; acesso a dispositivos de E/S; acesso controlado aos arquvivos; detecção de erro; segurança e contabilidade.</mark>
    - <mark style="background: crimson; font-weight: 500; color: white"> O SO pode ser visto como gerenciador de recusos. Segundo esse ponto de vista, o trabalho do SO é oferecer uma alocação controlada e ordenada de processadores, memóriaas, dispostivos de E/S e outros recursos. O gerenciamento destes recursos é feito no tempo e no espaço.</mark>

<br>


## _Fixação_: O que é gerenciamento (multiplexação) no tempo e gerenciamento no espaço?
- Resposta:
    - Quando um recurso é gerenciado (multiplexado) no **tempo**, diferentes programas ou usuários se revezam usando-o. Primeiro um deles usa o recurso, então outro e assim por diante. Exemplo: Apenas uma CPU e múltiplos programas querendo ser executados nela, o sistema operacional primeiro aloca a CPU para um programa, então, após ele ter sido executado por tempo suficiente, outro programa passa a fazer uso da CPU, então outro, e finalmente o primeiro de novo
    - No gerenciamento (multiplexação) no **espaço**, os clientes em vez de revezarem, cada um tem direito a uma parte do recurso. Exemplo: A memória principal é normalmente dividida entre vários programas sendo executados, de modo que cada um pode ser residente ao mesmo tempo. Presumindo que há memória suficiente para manter múltiplos programas, é mais eficiente manter vários programas na memória ao mesmo tempo do que dar a um deles toda ela, especialmente se o programa precisa apenas de uma pequena fração do total.


<br>

## 2. Explique detalhadamente a técnica de multiprogramação, apontando os suas vantagens e desvantagens (a questão oficial só pergunta sobre as vantagens, a desvantagem foi de minha autoria no enunciado).
- Resposta:
    - Multiprogramação **é a capacidade de um computador para executar mais de um programa de cada vez**. Os programas compartilham os recursos do computador, mas cada programa tem sua própria área de memória na qual armazena suas instruções e dados.
    - **Vantagens:** Permitem que a CPU seja usada de forma mais eficiente, executando vários programas ao mesmo tempo. Também permitem melhor utilização da memória através da partilha de memória entre vários programas. Assim como permitem maior flexibilidade em termos de programação e execução de programas.
    - **Desvantagens:** Podem ser mais complexos de projetar e implementar do que sistemas operacionais de programação única. Também podem ser mais difíceis de depurar e solucionar problemas. Além disso, sistemas operacionais multiprogramação podem levar ao aumento do uso de CPU e memória se não forem usados corretamente.
- Gabarito da professora:
    - <mark style="background: crimson; font-weight: 500; color: white"> Os sistemas monoprogramáveis se caracterizam por permitir que o processador,a memória e os periféricos permaneçam exclusivamente dedicados à execução de um único programa. Nos sistemas multiprogramáveis ou multitarefa, os recursos computacionais são compartilhados entre os diversos usuários e aplicações. Enquanto em sistemas monoprogramáveis existe apenas um programa utilizando os recursos disponíveis, nos multiprogramáveis várias aplicações compartilham esses mesmos recursos.
    - <mark style="background: crimson; font-weight: 500; color: white"> As vantagens do uso de sistemas multiprogramáveis são a reduçãodo tempo de resposta das aplicações processadas no ambiente e a redução dos custos, a partir do compartilhamento dos diversos recursos do sistema entre as diferentes aplicações.

<br>

## _Fixação:_ Explique multiprocessamento, diferencie de multiprogramação. Aponte as vantagens e desvantagens de multiprocessamento.
- Resposta:
    - É uma técnina na qual um sistema computacional utiliza múltiplos processadores ou núcleos de processamento para executar tarefas simultaneamente. Já multiprogramação é a capacidade de um computador para executar mais de um programa de cada vez. Os programas compartilham os recursos do computador, mas cada programa tem sua própria área de memória na qual armazena suas instruções e dados.
    - **Vantagens:** Melhor desempenho, pois os vários processadores ou núcleos permitem executar tarefas simultaneamente. Maior capacidade de processamento, é possível lidar com cargas de trabalho intensivas e executar programas complexos de forma mais eficiente.
    - **Desvantagens:** Complexidade de programação, a programação para sistemas multiprocessados pode ser mais complexa do que a programação para sistemas de processamento sequencial. Overhead de comunicação, em sistemas multiprocessados, os processadores ou núcleos precisam se comunicar e compartilhar dados entre si. Isso pode resultar em um overhead de comunicação, que é o tempo e recursos adicionais necessários para a sincronização e transferência de dados, podendo afetar o desempenho geral.

<br>

## 3. Qual o número máximo de células endereçadas em arquiteturas com REM de 16, 32 e 64 bits?

- A especificação do endereço de uma célula de memória é realizada através do registrador MAR (memory address register). Assim, a unidade de controle sabe qual célula de memória será acessada. O número de células endereçáveis é limitado pelo tamanho do MAR (n bits endereça 2n células).
    - MAR = 16 bits número max células = 2^16
    - MAR = 32 bits número max células = 2^32
    - MAR = 64 bits número max células = 2^64

<br>

## 4. Conceitue memória cache e apresente as principais vantagens no seu uso. Fale sobre o princípio da localidade.
- Resposta:
    - A memória cache é um tipo de memória de alta velocidade presente em muitos sistemas de computadores, como processadores e sistemas de armazenamento. Utilizada para armazenar temporariamente dados e instruções frequentemente acessados pelo processador, de forma a acelerar o acesso a esses dado e melhor o desempenho do sistema.
    - A função principal da memória cache é reduzir o tempo de acesso à memória principal (RAM), que é relativamente mais lenta em comparação com a memória cache. A ideia é que os dados e as instruções frequentemente usados sejam armazenados na memória cace, tornando-os prontamente disponíveis para o processador, sem a necessidade de acessar a memória principal.
    - Localidade espacial: Isso significa que os dados próximos a uma determinada localização de memória têm maior probabilidade de serem acessados em breve. A memória cache aproveita essa localidade espacial, armazenando blocos de dados adjacentes na memória principal em suas linhas de cache, permitindo que os dados adjacentes sejam acessados mais rapidamente.
    - Localidade temporal: Isso significa que os dados acessados recentemente têm maior probabilidade de serem acessados novamente em um futuro próximo. A memória cache também aproveita essa localidade temporal, mantendo os dados recentemente acessados disponíveis para acesso rápido.

- Gabarito da professora:
    - <mark style="background: crimson; font-weight: 500; color: white"> A memória cache é uma memória volátil, de alta velocidade, porém com pequena capacidade de armazenamento. O tempo de acesso a um dado nela contido é muito menor que se o memso estivesso na memória principal. O propósito do uso da memória cache é minimiza a disparidade existente entre a velocidade com que o processador e a velocidade com que os dados são acessados na memória principal
    - <mark style="background: crimson; font-weight: 500; color: white"> O princípio da localidade é a tendência do processador referenciar instruções e dados na memória principal localizados em endereços próximos. Por exemplo, esta tendência pode ser justificad pela alta incidência de estruturas de repetição e acessos a vetores. Assim o princípio da localidade garante que após a transferência de um bloco da MP para a cache, haverá alta probabilidade de cache hits em futuras referências.


## _Fixação:_ Defina técnica de pipelining?

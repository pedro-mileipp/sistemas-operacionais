# **_CRONOGRAMA DE ESTUDOS PARA S.O_**

## Até dia 26 para terminar Sincronização de Processos:
- Ver as vídeos aulas [], anotar todos os tópicos importantes, procurar exemplos de semáforos na internet [] e resolver questinário usando o ChatGPT para elaborar perguntas [].

## Do dia 27/06 à 30/6  terminar Deadlock: 
- Ver as vídeos aulas [], anotar sobre os tópicos [], procurar exemplos de deadlocks na internet [] e resolver questinário usando o ChatGPT para elaborar perguntas. []

<br>

# *Anotações*

## Comunicação entre processos

- Processos precisam trabalhar colaborativamente e se comunicar para atingir um objetivo comum, processos não são independentes;
- Podem haver conflitos, assim como um processo pode invadir o espaço do outro;
- Se um processo não está pronto para comunicar, o outro processo precisa abortar até que o outro esteja pronto;
- Condição de Corrida:
  1. Situação onde dois ou mais processos acessam recursos compartilhados concorrentemente;
  2. Há uma corrida pelo recurso;
  3. Ex: lendo ou escrevendo algum dado compartilhado e o resultado depende de quem processa no momento propício
  4. a = d + c;
  5. x = a + y (a variável 'a' é compartilhado/race cond.);
  6. Dois ou mais processos acessam recursos de forma competitiva.
- Outro exemplo:
  - Operador OP1 (no Brasil) lê Poltrona1 vaga;
  - Operador OP2 (no Japão) lê Poltrona1 vaga;
  - Operador OP1 compra a Poltrona1 -> X;
  - *Operador OP2 compra a Poltrona1* -> problema de sincronização. 
- Região Crítica, definição:
  - <mark style="background: purple; color: white; font-weight: 500">N processos competindo para utilizar os mesmos dados compartilhados, a região crítica será o segmento de código de cada processo onde é feito o acesso a este dado compartilhado.</mark>
  - O problema é garantir que quando um processo executa a sua região crítica, nenhum outro processo pode acessar a sua região crítica, ou seja, **evitar condições de corrida**.
- Vários processos acessam dados compartilhados concorrentemente e o resultado da execução depende da ordem específica em que ocorre o acesso ao dado compartilhado
- _Exclusão Mútua_:
 - Se um processo P está executando sua região crítica nenhum outro poderá executar a sua região crítica, ou seja, impedir que mais de um processo leia e escreva em uma variável compartilhada ao mesmo tempo.
 - Regras para saber se uma solução de exclusão mútua seja boa:
   1. Dois processos nunca podem estar simultaneamente dentro de suas regiões críticas;
   1. Não se pode fazer suposições em relação à velocidade e ao número de CPUs;
   1. Um processo fora da região crítica não deve caussar bloqueio a outro processo;
   1. Um processo não pode esperar eternamente par entrar em sua região crítica;
- _Progresso:_ Nenhum processo fora de sua região crítica pode bloquear outro processo
- _Espera Limitada:_ Um processo não pode esperar indefinidamente para entrar em sua região crítica
- Produtor X Consumidor:
  - O Produtor é um processo que grava as informações em um buffer compartilhadpo, cada item gerado preenche uma posição no buffer. 
  - O Consumidor é um processo que usa as informações gravadas no buffer. Cada item consumido libera uma posição no buffer.
  - O Produtor pode produzir um item enquanto o consumidor está consumindo outro.
  - Os processos produtores e consumidores precisam estar sincronizados de forma que um produtor não consuma um item ainda não produzido.

<br>

## Soluções para evitar condições de corrida
- Desabilitar interrupções:
  - É a solução mais simples para se implementar a exclusão mútua.
  - Um processo antes de entrar na sua RC, desabilita todas as interrupcções.
  - Após a execução da RC, todas as interrupções são habilitadas novamente.
  ```python
  '''Desabilita Interrupções'''
    # -> Região Crítica
  '''Habilita interrupções'''
  ```
  - Desta forma, o processo garante acesso exclusivo ao recurso compartilhado
  - _Desvantagens_:
    - Não se deve dar ao processo do usuário o poder de desabilitar interrupções, se o processo não as reabilita o funcionamento do sistema está comprometido
    - As interrupções são desabilitadas em apenas uma CPU, outros processos podem continuar executando em outras CPUs e acessar os recursos compartilhados.
    - Exclui não somente processos conflitantes mas também todos os outros processos.

- Variável de Bloqueio - _mutex_:
  - Introduz uma variável lógica  que recebe TRUE quando o processo entra em sua região crítica.
  - Ao sair da região crítica a variável lógica recebe FALSE.
  ```c
  while(mutex);
  mutex = true;
  // Região Crítica
  mutex = false;
  ```
  - Logo, se a variável lógica estiver com TRUE, já existe um processo acessando a região crítica e outro processo não poderá accessá-la;
  - Se o processo for interrompido após o teste de _mutex_ e antes que o seu valor seja atualizado, o mecanismo pode falhar.
  - Assim, dois processos podem acessar suas regiões críticas concorrentemente.
  - **Não garante a Exclusão Mútua**.

- Variável de comutação - _Turn_
  ```c
  // ProcessoA
  while (turn != A);
  // Região Crítica A;
  turn = B;
  // Processamento longo
  ```
  ```c
  // ProcessoB
  while (turn != B);
  // Região Crítica B;
  turn = A;
  // Processamento curto
  ```
  - Garante a exclusão mútua, porém, possui o problema da espera ocupada;
  - Obriga alternar a execução entre as regiões críticas dos processos, se um processo executar sua RC com maior frequência, será prejuficado;
  - Um processo fora da sua RC "bloqueia" a execução de outro;
    - No exemplo anterior, o processo A realiza um processameto longo e não cede a vez para B;
    - Não garante o requisito de PROGRESSO.

- Comutação não alternada
  - Assegura a exclusão mútua entre dois processos sme precisar alternar a execução entre as suas regiões críticas;
  - Utiliza:
    - A variável _turn_ que indica qual processo está na vez de executar;
    - O vetor _Interested_ que indica para cada processo se ele está interessado e pronto para executar sua RC;
    - Um processo entra na sua região crítica somente se o outro não estiver interessado;
    - Caso os dois processos estejam interessados o valor de turn decide qual processo ganha a região crítica
    ```c
    // ProcessoA
    interested[A] = true;
    turn = B;
    while (interested[B] && turn==B);
    Região Crítica A;
    interested[A] = false;
    ```
    ```c
    // ProcessoB
    interested[B] = true;
    turn = A;
    while (interested[A] && turn==A);
    Região Crítica B;
    interested[B] = false;
    ```
  - Garante a exclusão mútua
  - Requisito de progresso é satisfeito
  - Requisito de espera limitada é satisfeito
  - Possui o problema da espera ocupada

- Problemas da espera ocupada:
  - **Definição:** A espera ocupada (busy-waiting) é uma técnica de programação em que um processo ou thread fica em um loop contínuo (um loop de espera) verificando repetidamente uma condição até que ela seja satisfeita. Em outras palavras, o processo fica "ocupado" verificando repetidamente se uma determinada condição é verdadeira antes de prosseguir com a execução.
  - O problema da espera ocupada é que ela resulta em um consumo excessivo de recursos do sistema, principalmente do processador. Quando um processo ou thread está em um loop de espera, ele usa ativamente o tempo do processador, mesmo que não esteja realizando qualquer tarefa útil. Isso desperdiça recursos valiosos, reduzindo a eficiência e o desempenho geral do sistema.
  - Outro problema é que a espera ocupada não é escalonável. Quando vários processos ou threads estão esperando ocupadamente, todos eles competem pelo processador, o que pode resultar em um aumento significativo do consumo de recursos e em uma degradação do desempenho geral do sistema.
  - A espera ocupada também pode causar bloqueios indesejados ou deadlocks. Se dois ou mais processos ou threads estão em espera ocupada e dependem uns dos outros para progredir, pode ocorrer uma situação em que todos eles ficam presos em loops de espera infinitos, resultando em um bloqueio completo do sistema.

- Solução para espera ocupada:
  - Introduzir comandos que permitam que um processo seja colocado em estado de espera quando ele não puder acessar a sua região crítica
  - O processo fica em estado de espera até que outro processo o libere
  - Semáforos
  - Monitores

<br>

## Semáforos
- Todas as soluções apresentadas possuem o problema da espera ocupada, o processo "bloqueado" (ele está impedido de entrar em sua região crítica, mas não está em estado de espera) consome tempo de CPU desnecessariamente.
- Exemplo:
  Quando um processo A está em sua RC e outro processo B desejar sua RC,e ste fica em loop, testando uma dada condição até que lhe seja permitido o acesso a sua RC.
  - Neste caso, o processo B consome tempo de CPU desnecessariamente.

<br>

- Um semáforo é uma variável inteira não negatica que pode ser manipulada por duas instruções P (Down) e V (Up)
- No caso da exclusão mútua as instruções Down e Up funcionam como protocolos de entrada e saída das regiões críticas.
- As modificações feitas no valor do semáforo usando Down e Up são atômicas, ou seja, quando um processo modificar o valor do semáforo, nenhum outro pode modificá-lo concorrentemente e são implementadas através de chamadas ao sistema. 
- _Down_ e _Up_ como protocolos de entrada e saída das RCs.
- _Down_ é executada quando o processo deseja entrar na RC. Decrementa o semáforo de 1.
- _Up_ é executada quando o processo sai da sua RC. Incrementa o semáforo de 1.

```c
Down(S)
  if(S == 0)
    // bloqueia processo
  else
    S = S - 1;

Up(S)
  if(tem processo na fila)
    // libera o processo da fila e ele entra na RC
  else
    S = S + 1;
```
- Um semáforo fica associado a um recurso compartilhado, indicando se ele está sendo usado
- Se o valor do semáforo é maior do que zero:
  - Existe recurso compartilhado disponível
  - processo pode usar o recurso e decrementa o semáforo
- Se o valor do semáforo é zero:
  - Os recursos disponíveis estão sendo usados
  - O processo deve entrar em estado de espera até que o recurso se torne disponível.
- No exemplo a seguir para a exclusão mútua é usado um semáforo binário (MUTEX)

|     P1            |    P2             | mutex |
| ----------------- | ----------------- | ----- |
|                   |                   |   1   |
| Down(mutex) **X** |                   |   0   |
|                   | Down(mutex) **X** | 0 -> Bloqueia P2 |
| RC1 - Acessa RC1  |                   |   0   |
| Up (mutex)        |                   | 0 -> Libera P2 |
|                   | RC2 -> Acessa RC2 |   0   |
|                   | Up(mutex)         |   1   |

- Produtor X Consumidor
  - O produtor é um processo que grava informações em um buffer compartilhado. Cada item gerado preenche uma posição do buffer.
  - O Consumidor é um procesos que usa as informações gravadas no buffer. Cada item consumido libera uma posição do buffer.
  - O produtor não pode escrever em um buffer cheio e o consumidor não pode ler um buffer vazio.
- Solução com Semáforos:
  - A solução proposta deve garantir a exclusão mútua e a sincronização condicional.
  - São usados 3 semáforos:
    - Full -> semáforo contador: indica a quantidade de posições cheias
    - Empty -> semáforo contador: indica a quantidade de posições vazias
    - Mutex -> semáforo binário: indica se o buffer está sendo usado
  - Se _Full = 0_, o buffer está vazio -> Bloqueia o consumidor
  - Se _Empty = 0_, o buffer está cheio -> Bloqueia o produtor

  ```c
  // Produtor
  Down(empty) // qtd de posições vazias, se estiver 0, nenhuma posição vazia e é bloqueado
  Down(mutex)
  Buffer[IN] = item
  IN = (IN+1) % BUFFER_SIZE
  Up(mutex)
  Up(full) // Coloca mais 1 no full pq tem mais um cheio
  
  // Consumidor
  Down (full) // se full == 0, indica 0 posições cheias, ou seja, tem nada
  Down (mutex)
  item = Buffer[OUT]
  OUT = (OUT+I) % BUFFER_SIZE
  Up(mutex)
  Up(empty) // Coloca uma variável vazia a mais, porque uma foi consumida
  ```
- Cuidado com os semáforos:
  - O uso de semáforos exige muito cuidado do programador
  - Os comandos down e up podem estar espalhados em um programa sendo difícil visualizar o efeito destas operações
  - Pode gerar deadlock ou starvation
  - Deadlock: dois ou mais processos estão bloqueados aguardando por um evento que só pode ser gerado por um dos processos bloqueados
  - Starvation: pode ocorrer caso a fila associada ao semáforo não seja FCFS

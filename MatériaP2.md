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
  '''
  
  Desabilita Interrupções
  -> Região Crítica
  Habilita interrupções

  '''
  ```
  - Desta forma, o processo garante acesso exclusivo ao recurso compartilhado
  - _Desvantagens_:
    - Não se deve dar ao processo do usuário o poder de desabilitar interrupções, se o processo não as reabilita o funcionamento do sistema está comprometido
    - As interrupções são desabilitadas em apenas uma CPU, outros processos podem continuar executando em outras CPUs e acessar os recursos compartilhados.
    - Exclui não somente processos conflitantes mas também todos os outros processos.

- Variável de Bloqueio - _mutex_:
  -







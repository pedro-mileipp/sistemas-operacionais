# Lista de exercícios para Prova 2

## Questões puramente teóricas

### **1. O que é deadlock, quais as condições para obtê-lo e quais as soluções possíveis?**
- Deadlock é a situação em que um processo aguarda por um recurso que nunca estará disponível ou um evento que não ocorrerá. Para que ocorra a situação de deadlock, quatro condições são necessárias simultaneamente: _exclusão mútua:_ cada recurso só pode estar alocado a um único processo, em um determinado instante; _posse e espera:_ um processo, além dos recursos já alocados, pode estar esperando por outros recursos; _não preempção:_ um recurso não pode ser liberado de um processo só porque outros desejam o mesmo recurso; _espera circular:_ um processo pode ter de esperar por um recurso alocado a outro processo e vice-versa. para prevenir a ocorrência de deadlocks, é necessário garantir que umas das 4 condições apresentadas nunca ocorra. Porém, prevenir evitando a ocorrência dessas condições é bastante limitado e por isso na prática não é utilizado. uma solução conhecida como Algoritmo do Banqueiro (implementada com a presença das 4 condições) também possui várias limitações, a maior delas é a necessidade de saber com antecedência o número fixo de processos ativos e de recursos disponíveis no sistema. Essa limitação impede que a solução seja implementada na prática, pois é muito difícil prever o número de usuários no sistema e o número de recursos disponíveis. Desta forma, é preciso detectar o deadlock e aplicar uma política para a recuperação do sistema. 

<br>

### **2. Suponha    um    sistema    computacional    com    64Kb    de    memória    principal    e    que    utilize    um    sistema operacional de 14Kb que implemente alocação contígua de memória. Considere também um programa de 90Kb, formado por um módulo principal de 20Kb e três módulos independentes, cada um com 10Kb, 20Kb e 30Kb**

### a. Como o programa poderia ser executado utilizando-se apenas a técnica de overlay? 
- O programa terá 50kb de memória para a execução do programa, que deverá ser dividida entre o módulo principal (20kb) e um espaço de overlay com tamanho em função do maior módulo (30kb).

### b. Se  o  módulo  de  30Kb  tivesse  seu  tamanho  aumentado  para  40Kb, seria possível executar o programa? Caso não possa, como o problema poderia ser contornado?
- Não. A únicas formas de executar seriam aumentar a quantidade de memória real ou dividir o módulo de 40kb em módulos menores independentes.

<br>

### **3.Qual a diferença entre fragmentação interna e externa da memória principal?**
- Fragmentação interna ocorre em espaços livres e contíguos na memória princiapl que são pré-alocados por processos, não possibilitando, portanto, o uso por outros processos. Fragmentação externa ocorre em espaços livres e contínuos, porém tão pequenos que não possibilitam a alocação de programas por processos.
- Fragmentação interna: ocorre quando um processo ou arquivo é alocado em uma partição ou bloco de memória maior que o necessário. Isso pode acontecer porque os sistemas operacionais alocam a memória em blocos fixos chamados "unidades de alocação" ou "páginas". Se um processo ou arquivo não preencher completamente o bloco alocado, a parte não utilizada do bloco é considerada fragmentação interna.
- Fragmentação externa: ocorre quando há espaços livres de memória ou espaço em disco suficiente para alocar um novo processo ou arquivo, mas esse espaço não está disponível em um único bloco contíguo. Em vez disso, o espaço livre fragmentado em várias partes menores e dispersas em diferentes locais do sistema. Uma solução para isso é a compactação, porém é um processo custoso.

<br>

### **4.Considerando as estratégias para escolha da partição dinamicamente, conceitue as estratégias first-fit, best-fit e worst-fit especificando prós e contras de cada uma.**
- First-fit: Escolhe o primeiro bloco livre de tamanho suficiente para cabar o programa. Neste algoritmo a lista de blocos livres é ordenanada por endereços. O algoritmo possui baixa complexidade.
- Best-fit: Escolhe o melhor bloco livre, ou seja, aquele em que o programa deixa o menor espaço sem utilização. O problema é que a tendência é deixar cada vez mais a memória com pequenos blocos livres, não contíguos, aumentando a fragmentação. Além do aumento da fragmentação, esta estratégia é mais custosa.
- Worst-fit: Escolhe o pior bloco livre, ou seja, aquele em que o programa deixa o maior espaço sem utilização. A ideia é deixar espaços maiores para que outros programas possam utilizá-los.

<br>

### **5.Considere um sistema que possua as seguintes área livres na memória  principal, ordenadas crescentemente:  10Kb, 4Kb, 20Kb, 18Kb, 7Kb, 9Kb, 12Kb e 15Kb. Para  cada  programa  abaixo,  qual seria a partição alocada utilizando-se as estratégias first-fit, best-fit e worst-fit?**

-  a. 12kb
- b. 10kb
- c. 9kb

    - First-fit: 20Kb, 10Kb, 18Kb
    - Best-fit: 12Kb, 10Kb, 9Kb
    - Worst-fit: 20Kb, 18Kb, 15Kb

<br>

### **6.Um sistema utiliza alocação particionada dinâmica como mecanismo de gerência de memória. O sistema operacional aloca uma área de memória total de 50Kb e possui, inicialmente, os programas da tabela a seguir:**


| Espaço  | Programas |
| ------------- |:-------------:|
| 5Kb     | Programa A     |
| 3Kb     | Programa B     |
| 10Kb     | Livre     |
| 6Kb     | Programa C     |
| 26Kb     | Livre     |

### Realize  as  operações  abaixo  sequencialmente,  mostrando  o  estado  da  memória  após  cada  uma  delas. Resolva a questão utilizando as estratégias best-fit, worst-fit e first-fit. 

### a) alocar uma área para o programa D que possui 6 Kb;
### b) liberar a área do programa A;
### c) alocar uma área para o programa E que possui 4 Kb.

<br>

- **Estratégia Best-fit:**
- a)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Programa A     |
    | 3Kb     | Programa B     |
    | 6Kb    | Programa D    |
    | 4Kb    | Livre   |
    | 6Kb     | Programa C     |
    | 26Kb     | Livre     |
- b) 
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Livre    |
    | 3Kb     | Programa B     |
    | 6Kb    | Programa D    |
    | 4Kb    | Livre   |
    | 6Kb     | Programa C     |
    | 26Kb     | Livre     |
- c)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Livre     |
    | 3Kb     | Programa B     |
    | 6Kb    | Programa D    |
    | 4Kb    | Programa E   |
    | 6Kb     | Programa C     |
    | 26Kb     | Livre     |

<br>

- **Estratégia Worst-fit:**

- a)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Programa A     |
    | 3Kb     | Programa B     |
    | 10Kb     | Livre     |
    | 6Kb     | Programa C     |
    | 6Kb     | Programa D     |
    | 20Kb     | Livre    |
- b)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Livre     |
    | 3Kb     | Programa B     |
    | 10Kb     | Livre     |
    | 6Kb     | Programa C     |
    | 6Kb     | Programa D     |
    | 20Kb     | Livre    |
- c)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Livre     |
    | 3Kb     | Programa B     |
    | 10Kb     | Livre     |
    | 6Kb     | Programa C     |
    | 6Kb     | Programa D     |
    | 4Kb     | Programa E    |
    | 16Kb     | Livre    |

<br>

- **Estratégia First-Fit:**
- a)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Programa A     |
    | 3Kb     | Programa B     |
    | 6Kb    | Programa D    |
    | 4Kb    | Livre    |
    | 6Kb     | Programa C     |
    | 26Kb     | Livre     |
- b)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Livre     |
    | 3Kb     | Programa B     |
    | 6Kb    | Programa D    |
    | 4Kb    | Livre    |
    | 6Kb     | Programa C     |
    | 26Kb     | Livre     |
- c)
    | Espaço  | Programas |
    | ------------- |:-------------:|
    | 5Kb     | Programa E     |
    | 1Kb     | Livre    |
    | 3Kb     | Programa B     |
    | 6Kb    | Programa D    |
    | 4Kb    | Livre    |
    | 6Kb     | Programa C     |
    | 26Kb     | Livre     |

<br>
<br>

### **7.O que é swapping e para que é utilizada esta técnica?  Qual a importância da realocação dinâmica nesta técnica?**
- A técnica de swapping foi introduzida para contornar o problema da insuficiência de memória principal. Essa técnica é aplicada à gerência para programas que esperam por memória livre para serem executados. Nesta situação, o sistema escolhe um processo residente, que é transferido da memória principal para a memória secundária (swap out), geralmente disco. Posteriormente, o processo é carregado de volta da memória secundária para a memória principal (swap in) e pode continuar sua execução como se nada tivesse acontecido. A realocação dinâmica permite que os programas possa ser retirados da memória principal para a memória secundária e trazidos novamente para a memória principal em qualquer posição.

<br>

### **Fixação: Conceitue memória virtual.**
- Memória virtual é um mecanismo utilizado pelos sistemas operacionais para permitir que os processos acessem uma quantidade maior de memória do que a memória física (RAM) disponível no ssitema. A ideia por trás da memória virtual é proporcionar uma ilusão aos processos de que eles têm acesso a uma grande quantidade de memória, mesmo que o espaço real de memória seja limitado.
- A memória virtual funciona combinando a memória RAM do computador com uma área de armazenamento em disco chamada de "espaço de troca" (swap space). Quando um procesos é executado e precisa de mais memória do que a disponível na RAM, partes menos utilizadas da memória são movidas para o espaço de troca, liberando espaço na RAM para o nov conteúdo necessário.

<br>

### **8.Quais  os  benefícios  oferecidos  pela  técnica  de  memória  virtual?  Como  este  conceito  permite  que  um programa e seus dados ultrapassem os limites da memória principal?**
- Os principais benefícios da técnica de memória virtual são possibilitar que programas e dados sejam armazenados independente do tamanho da memória principal. Esta técnica sofisticada de gerência de memória combina as memórias principal e secundária, dando ao usuário a impressão de existir uma memória muito maior do que a MP. 

<br>

### **9. Qual a principal diferença entre os sistemas que implementam paginação e segmentação?**
- A principal dferença entre os dois sistemas está relacionada na forma como o espaço de endereçamento virtual está dividido logicamente. Na paginação, o espaço de endereçamento está divido em blocos com o mesmo número de endereços virtuais (páginas), enquanto que na segmentação o tamanho dos blocos pode variar (segmentos).

<br>

### **10. O  que  são  tabelas  de  páginas  e  tabelas  de  segmentos?  Explique  para  que  servem  os  bits  de  validade, referencia e modificação encontrados nestas tabelas.**

- São tabelas de mapeamento, utilizadas no mecanismo de memória virtual, que possibilitam que endereços virtuais sejam traduzidos em endereços reais. O bit de validade é usado para indicar se a página ou o segmento em questão encontra-se na memória principal. O bit de modificação, indica 1 quando a página foi escrita na memória principal e 0, caso contrário. O bit de referência indica se a página foi referenciada na memória principal.

<br>

### **11.O  que  é  um  page  fault,  quando  ocorre  e  quem  controla  a  sua  ocorrência?  Como  uma  elevada  taxa  de page fault pode comprometer o sistema operacional?** 

- O page fault ocorre todas as vezes que um processo faz referência a um endereço virtual pertencente a uma página virtual que não se encontra mapeada em uma página real, ou seja, não está, no momento, na memória principal. A ocorrência do page fault é verificada através do bit de validade presente na entrada da tabela de páginas referente à página virtual. Uma elevada taxa de page fault pode comprometer o desempenho do sistema devido ao excessivo overhead de operações E/S gerados pela paginação.

<br>

### **12.Compare as políticas de busca de páginas apresentadas.**
- Na paginação por demanda, as páginas dos processos são transferidas da memória secundária para a principal apenas quando são referenciadas. Este mecanismo é conveniente, na medida em que leva para a memória principal apenas as páginas realmente necessárias à execução do programa. Desse modo, é possível que partes não executadas do programa, como rotinas de tratamento de erros, nunca sejam carregadas para a memória.
- Na página antecipada, o sistema carrega para a memória principal, além das páginas referenciadas, outras páginas que podem ou não ser necessárias ao processo ao longo do seu processamento. Se imaginarmos que o programa está armazenado sequencialmente no disco, existe grande economia de tempo em levar um conjunto de páginas da memória secndária, ao contrário de carregar umad e cada vez. Por outro lado, caso o processo não precise das páginas carregadas antecipadamente, o sistema terá perdido tempo e ocupado memória principal desnecessariamente.

<br>

### **13.Quais as vantagens e desvantagens da alocação de páginas variável comparada à alocação fixa?**
- A política de alocação de páginas determina quantos quadros (frames) um processo pode manter na memória principal. 
- Na alocação fixa cada processo tem um número máximo de frames, que pode ser usado durante a execução. É uma política simples de ser implementada, mas não é sempre uma boa opção, pois os processos possuem necessidades diferentes na alocação de memória. Se o número de frames alocado para um processo for pouco, uma página do próprio processo deve ser descartada para que outra seja carregada. O limite de frames deve ser definido no momento da criação do processo com base no tipo de aplicação que será executada. Se o limite for pequeno, o processo terá alto índice de page faults; se o limite for alto, poucos processos compartilharão a memória, podendo aumentar o swapping de processos. 
- Na alocação variável o número máximo de frames alocado para um processo durante a sua execução pode variar. Um processo com alta taxa de paginação pode ter o limite máximo de frames aumentado para diminuir o alto índice de page faults. Já um processo com baixa taxa de paginação pode ter seus frames alocados para outros processos. A alocação variável é mais flexível, mas exige que o sistema operacional monitore constantemente o comportamento do s processos, gerando maior overhead.

<br>


### 14.Um  sistema  com  gerência  de  memória  virtual  por  paginação  possui  tamanho  de  página  com  512 posições, espaço de endereçamento virtual com 512 páginas e memória real com 10 frames. Diga como é o formato do endereço virtual e o formato do endereço real.

- Tamanho da página: 512 posições
- Espaço de endereçamento virtual: 512 páginas
- Memória real: 10 frames

<br>

- **Formato de endereço virtual**
  - Como temos 512 páginas no espaço de enderaçamento virtual, são necessários 9 bits para representar o número da página virtual (2^9=512). Os primeiros 9 bits do formato indicam a página virtual.
  - O tamanho da página é de 512 posições, então serão necessários mais 9 bits para representar o deslocamento dentro da página (2^9=512). Portanto os próximos 9 bits do endereço virtual indicam o deslocamento.
  ```
    |-------------|----------------|
    | Número da   |   Deslocamento |
    | página      |   dentro da    |
    | virtual     |    página      |
    |-------------|----------------|
    |    9 bits   |     9 bits     |
  ```
- **Formato de endereço real**
  - Temos 10 frames, portanto são necessários  4 bits para representar o número de frames (2^4=16).
  - O tamanho da página e o tamanho do frame são iguais, portanto 9 bits para o deslocamento no frame
  ```
  |-----------|----------------|
  | Número do |   Deslocamento |
  | frame     |   dentro do    |
  |           |    frame       |
  |-----------|----------------|
  |   4 bits  |     9 bits     |
  ```

### **15. Um    sistema operacional    implementa    gerência    de    memória    virtual    por    paginação.    Considere  endereços  virtuais  com  16  bits,  referenciados  por  um  mesmo  processo  durante  sua  execução  e  sua tabela de páginas abaixo  com  no  máximo  256  entradas,  sendo  que  estão  representadas  apenas  as  páginas  presentes  na memória  real.  Indique  para  cada  endereço  virtual  a  seguir  a  página  virtual  em  que  o  endereço  se encontra e o respectivo deslocamento. Os endereços virtuais são 2047, 1098, 451.**

- 256 entradas na tabela de páginas significa que há 256 páginas, portanto serão necessários 8 bits para o número de páginas (2^8=256). Como o endereço é formado por 16 bits, sobra 8 bits para o deslocamento.

- a) 2047
  ```
  | Página virtual | Deslocamento |
  |   00000111     |  11111111    |
  ```    
  - Página virtual 7; Deslocamento 255

- b) 1098
  ```
  | Página virtual | Deslocamento |
  |   00000100     |  01001010    |
  ```    
  - Página virtual 4; Deslocamento 74

- c) 451
  ```
  | Página virtual | Deslocamento |
  |   00000001     |  11000011    |
  ```    
  - Página virtual 1; Deslocamento 195

<br>

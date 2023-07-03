# Lista de exercícios para Prova 2

## Questões puramente teóricas

### **1. O que é deadlock, quais as condições para obtê-lo e quais as soluções possíveis?**
- Deadlock é a situação em que um processo aguarda por um recurso que nunca estará disponível ou um evento que não ocorrerá. Para que ocorra a situação de deadlock, quatro condições são necessárias simultaneamente: _exclusão mútua:_ cada recurso só pode estar alocado a um único processo, em um determinado instante; _posse e espera:_ um processo, além dos recursos já alocados, pode estar esperando por outros recursos; _não preempção:_ um recurso não pode ser liberado de um processo só porque outros desejam o mesmo recurso; _espera circular:_ um processo pode ter de esperar por um recurso alocado a outro processo e vice-versa. para prevenir a ocorrência de deadlocks, é necessário garantir que umas das 4 condições apresentadas nunca ocorra. Porém, prevenir evitando a ocorrência dessas condições é bastante limitado e por isso na prática não é utilizado. uma solução conhecida como Algoritmo do Banqueiro (implementada com a presença das 4 condições) também possui várias limitações, a maior delas é a necessidade de saber com antecedência o número fixo de processos ativos e de recursos disponíveis no sistema. Essa limitação impede que a solução seja implementada na prática, pois é muito difícil prever o número de usuários no sistema e o número de recursos disponíveis. Desta forma, é preciso detectar o deadlock e aplicar uma política para a recuperação do sistema. 
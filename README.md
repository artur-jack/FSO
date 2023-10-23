# Conceitos

## Estados de um processo

- Rodando
- Bloqueado
- Pronto
  
## Preempção

O escalonador pode ser preemptivo ou não preemptivo. Onde a preempção é a suspensão temporária da execução de um processo.

## Critérios de Escalonamento

- Justiça:
  Garantir que todos os processos terão chances justas de uso de processador. Não são chances iguais.
  
- Eficiência:
  Quando existir trabalho a fazer, o processador deve estar ocupado.

- Minimizar o tempo de resposta:
  reduz o tempo entre a entrada de usuário e a resposta dada.
  
- Minimizar o turnaround:
  reduzir o tempo do lançamento do processo até seu término.
  
- Minimizar waiting time:
  minimizar o tempo de espera pela CPU.
  
- Maximizar throughtput:
  Maximizar o número de tarefas executados em uma unidade de tempo.

# Algoritmos de Escalonamento

- First Come First Served
- Round-Robin
- Prioridades
- Shortest Job First

## First Come First Served

É um escalonamento não-preemptivo (não há tempo limite de uso de CPU) onde basicamente o processo que obtém a CPU segue a ordem de chegada utilizando a política FIFO (First-In 
First-Out).

- Vantagens: 
  - Simples de ser implementado
  - Algoritmo eficiente: a CPU sempre é utilizada
  
- Desvantagens:
  - Impossibilidade de se prever quando um processo vai 
  iniciar
  - Tempo média de espera de processos não é priorizado
  - Processos que usam muito a CPU levam vantagens sobre 
  processos que causam muito seu bloqueio


## Round-Robin (alternância circular)

Cada processo tem o direito de usar o processador por um intervalo de tempo prédefinido. Este intervalo de tempo é denominado quantum. Onde quando o quantum acaba o processador é dado a outro processo.

- Um dos maiores problemas do algoritmo de escalonamento round-robin diz a respeito da determinação de um bom valor a ser atribuído ao quantum
- Para determinar esse valor, deve-se considerar o tempo médio da troca de contexto e o tempo de resposta desejado
  - Qual a influência que o tempo da troca de contexto?
- Quantum padrão 100 ms

## Escalonamento com Prioridades

Atribuí prioridades a cada processo. Onde processo com maior prioridade rodam primeiro.

As prioridades podem ser atribuídas de duas formas: estática ou dinâmica

- Estática: os processos são divididos em classes e a cada classe é atribuída uma prioridade. A cada prioridade existe uma fila de prontos associada.
- Dinâmica: o sistema analisa o comportamento dos processos e atribui prioridades favorecendo um certo tipo de comportamento
  - Processos I/O devem possuir prioridade alta
  - Prioridade dinâmica: 1/f, onde f é a fração do quantum de tempo usada na última rodada do processo

## Shortest Job First

Algoritmo projetado para sistemas em lote. A ideia é dado um conjunto de processos, execute os de menor tempo de execução antes.
- Reduzir o tempo de turnaround (tempo de lançamento do processo até seu término)
- Requer que o tempo total de execução do processo seja conhecido antes do seu início

# Trheads

São meio que um processo mais leve do que o processe tradicional. 

# Condição de Corrida

É um problema que ocorre quando acontece uma troca de contexto em um região crítica envolvendo memória compartilhada entre os processo. Onde a troca de contexto pode afetar o resultado das operações de dois processos que estão alterando a mesma região de memória. 

As condições de corrida levam a resultados inesperados e devem ser evitadas. Precisando, assim, assegurar que os processos que estejam trabalhando na mesma região de memória não sejam interrompidos, ou aguardem o término do outro processo antes de iniciar suas atividades. (Esse processo é conhecido como **exclusão mútua**).

## Técnicas de Implementação de Exclusão Mútua

- Inibir Interrupções
  
- Com espera ocupada:
  
  - Estrita Alternância
  - Algoritmo de Peterson
  - Utilizar hardware adicional
   
- Com bloqueio de processos:
  
  - Semáforos
  - Mutexes
  - Locks
  - Monitores
  - Variáveis de condição
    
# DeadLock

É um problema que ocorre quando os programas/threads aguardam um recurso que não é liberado

- Starvation: quando os mecanismos de sincronização não permitem que o programa avance
- Em geral, deadlocks ocorrem em recursos não-preemptíveis(Um recurso que não pode ser tomado à força, onde o processo que o possui deve liberá-los espontaneamente).
- Em recursos preemptíveis a simples transferência de recursos os resolve.

**Definição formal de deadlock:**
“Um conjunto de processos estará em situação de deadlock se cada processo no conjunto estiver esperando por um evento que apenas outro processo no conjunto pode causar”

Então como todos os processos estão esperando, nenhum deles poderá causar qualquer evento que possa despertar outros membros do conjunto, e todos os processos continuam esperando para sempre.

## Condições para ocorrência de DeadLock
Segundo Coffman et al. (1971) existem quatro condições para ocorrer um deadlock:

1- Exclusão Mútua:  cada recurso está associado a um processo ou está disponível.

2- Posse e espera:  processo atualmente de posse de recursos que foram concedidos antes podem solicitar novos recursos.

3- não-preempção:  recursos concedidos antes não podem ser liberados à força.

4- Espera circular:  deve haver uma lista circular de dois ou mais processos esperando por recursos detido pelo próximo membro da cadeia.

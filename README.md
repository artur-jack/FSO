# Conceitos

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
  – Simples de ser implementado
  – Algoritmo eficiente: a CPU sempre é utilizada
  
- Desvantagens:
  – Impossibilidade de se prever quando um processo vai 
  iniciar
  – Tempo média de espera de processos não é priorizado
  – Processos que usam muito a CPU levam vantagens sobre 
  processos que causam muito seu bloqueio


## Round-Robin (alternância circular)

Cada processo tem o direito de usar o processador por um intervalo de tempo prédefinido. Este intervalo de tempo é denominado quantum. Onde quando o quantum acaba o processador é dado a outro processo.

- Um dos maiores problemas do algoritmo de escalonamento round-robin diz a respeito da determinação de um bom valor a ser atribuído ao quantum
- Para determinar esse valor, deve-se considerar o tempo médio da troca de contexto e o tempo de resposta desejado
  – Qual a influência que o tempo da troca de contexto?
- Quantum padrão 100 ms

## Escalonamento com Prioridades

Atribuí prioridades a cada processo. Onde processo com maior prioridade rodam primeiro.

As prioridades podem ser atribuídas de duas formas: estática ou dinâmica

- Estática: os processos são divididos em classes e a cada classe é atribuída uma prioridade. A cada prioridade existe uma fila de prontos associada.
- Dinâmica: o sistema analisa o comportamento dos processos e atribui prioridades favorecendo um certo tipo de comportamento
  – Processos I/O devem possuir prioridade alta
  – Prioridade dinâmica: 1/f, onde f é a fração do quantum de tempo usada na última rodada do processo

## Shortest Job First

Algoritmo projetado para sistemas em lote. A ideia é dado um conjunto de processos, execute os de menor tempo de execução antes.
- Reduzir o tempo de turnaround (tempo de lançamento do processo até seu término)
- Requer que o tempo total de execução do processo seja conhecido antes do seu início

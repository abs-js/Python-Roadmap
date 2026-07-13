# Capítulo 65: Heapq (Filas de Prioridade) – A Ordem de Importância

### Teoria Sem Enrolação
Listas comuns são ótimas para ordem de chegada, mas péssimas para ordem de **importância**. O módulo **`heapq`** implementa uma "Fila de Prioridade" usando um algoritmo chamado *Min-Heap*. 
- O menor elemento da lista está sempre na posição `[0]`.
- Quando você retira o menor (`heappop`), o Python reorganiza a fila de forma ultra eficiente (muito mais rápido que dar um `.sort()` a cada mudança).
- É ideal para gerenciar tarefas onde o que tem o menor valor (ou maior urgência) deve ser processado primeiro.

### A Grande Analogia
Imagine uma **Triagem de Pronto-Socorro**. 
As pessoas não são atendidas por ordem de chegada se houver alguém com um ferimento grave. O **`heapq`** é o enfermeiro da triagem. Ele mantém os pacientes organizados. Sempre que um consultório libera, ele olha para a lista e pega quem tem o "nível de dor" mais baixo (ou alto, dependendo da sua convenção). Mesmo que cheguem 100 pessoas novas, o enfermeiro sabe instintivamente quem é o próximo a ser chamado sem ter que reorganizar todas as cadeiras da sala de espera.

### Desafio de Aplicação CLI: "O Organizador de Tarefas Urgentes"
Crie um sistema de tarefas onde cada tarefa tem um nome e um nível de prioridade (número). 
1. Use `heapq.heappush` para adicionar 3 tarefas.
2. Lembre-se: O `heapq` prioriza números menores.
3. Use `heapq.heappop` para imprimir as tarefas na ordem da mais prioritária para a menos prioritária.

### Gabarito do Desafio
```python
import heapq

# Uma lista vazia que servirá como nosso heap
tarefas = []

# Adicionando tarefas (Prioridade, Nome)
# Quanto menor o número, maior a prioridade
heapq.heappush(tarefas, (3, "Limpar a casa"))
heapq.heappush(tarefas, (1, "Pagar servidor"))
heapq.heappush(tarefas, (2, "Estudar Python"))

print("--- EXECUÇÃO DE TAREFAS ---")

while tarefas:
    # Retira sempre quem tem a maior prioridade (menor número)
    prioridade, nome = heapq.heappop(tarefas)
    print(f"Executando agora: {nome} (Prioridade: {prioridade})")
```

### Quiz de Fixação
1. Onde fica guardado o menor elemento em um heap criado com `heapq`?  
   > **Resposta:** No índice `0` da lista.
2. Qual a vantagem de usar `heapq.heappush` em vez de `lista.append()` seguido de `lista.sort()`?  
   > **Resposta:** Performance. O heap mantém a estrutura organizada em tempo logarítmico, enquanto o sort é muito mais lento em listas grandes.
3. Como você faria para priorizar o maior número em vez do menor usando `heapq`?  
   > **Resposta:** Multiplicando os valores de prioridade por -1 ao inserir.

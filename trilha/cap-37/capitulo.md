# Capítulo 37: AsyncIO — A Dança da Eficiência (Programação Assíncrona)

### Teoria Sem Enrolação
Enquanto o *Multithreading* delega tarefas para vários braços, o **AsyncIO** trabalha com o conceito de **cooperação**. 
- **`async def`**: Define uma função como uma "corrotina". Ela pode ser pausada.
- **`await`**: Abre um ponto de pausa. O programa diz: "Vou esperar isso aqui terminar, pode cuidar de outras coisas enquanto isso".
- **Event Loop**: É o maestro que gerencia essas pausas, pulando de uma tarefa para outra sempre que uma delas fica "esperando" (por um download, um temporizador ou leitura de disco). 
É a base do desenvolvimento web moderno (FastAPI, por exemplo).

### A Grande Analogia
Imagine um **Garçom em um Café de um Homem Só**. 
Se ele trabalhasse de forma síncrona (comum), ele colocaria o café no filtro e ficaria parado olhando a água descer, sem atender mais ninguém até o café ficar pronto. 
No modo **AsyncIO**, o garçom coloca o café para filtrar (**await**), mas em vez de ficar parado, ele se vira e anota o pedido de outro cliente. Quando o café termina de filtrar, ele volta lá e entrega. Ele é uma pessoa só (um único processo/thread) fazendo o trabalho de 10, porque ele nunca fica parado esperando.

### Desafio de Aplicação CLI: "O Buffet Assíncrono"
Crie três funções assíncronas: `preparar_cafe()`, `preparar_torrada()` e `limpar_mesa()`. 
- Use `asyncio.sleep()` para simular os tempos de cada tarefa.
- Use `asyncio.gather()` para disparar as três tarefas ao mesmo tempo e veja como o tempo total é apenas o tempo da tarefa mais longa, e não a soma de todas.

### Gabarito do Desafio
```python
import asyncio
import time

async def preparar_cafe():
    print("Iniciando café...")
    await asyncio.sleep(3) # Pausa cooperativa
    print("Café pronto!")

async def preparar_torrada():
    print("Iniciando torrada...")
    await asyncio.sleep(2)
    print("Torrada pronta!")

async def main():
    inicio = time.time()
    # gather executa as corrotinas simultaneamente
    await asyncio.gather(preparar_cafe(), preparar_torrada())
    fim = time.time()
    print(f"Café da manhã completo em {fim - inicio:.2f} segundos!")

# Para rodar o loop assíncrono
asyncio.run(main())
```

### Quiz de Fixação
1. Qual a palavra-chave usada para pausar uma corrotina e ceder o controle de volta ao event loop?
   > **Resposta:** `await`.
2. O `asyncio.sleep(1)` bloqueia todo o programa como o `time.sleep(1)` faz?
   > **Resposta:** Não. O `asyncio.sleep` avisa ao loop que ele pode executar outras tarefas enquanto o tempo não passa.
3. Posso usar `await` dentro de uma função normal definida com `def`?
   > **Resposta:** Não, o `await` só pode ser usado dentro de funções definidas com `async def`.

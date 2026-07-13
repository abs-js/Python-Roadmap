# Capítulo 36: Multithreading vs Multiprocessing — O Time de Operários

### Teoria Sem Enrolação
O Python normalmente executa uma coisa por vez. Para ganhar velocidade, usamos:
- **Multithreading:** Várias "linhas de execução" dentro do mesmo processo. É excelente para tarefas que envolvem **espera** (I/O Bound), como baixar arquivos da internet ou ler do disco. O Python "pula" para outra tarefa enquanto espera o site responder.
- **Multiprocessing:** Cria vários processos separados, cada um com sua própria memória e usando um núcleo diferente da sua CPU. É ideal para **cálculos pesados** (CPU Bound), ignorando a trava de segurança do Python chamada GIL (Global Interpreter Lock).

### A Grande Analogia
Imagine uma **Cozinha de Restaurante**.
- **Multithreading** é um **Chef Único com vários braços**: enquanto a água parou para ferver, ele usa o outro braço para picar cebola. Ele não faz tudo ao mesmo tempo, mas aproveita os tempos de espera. Se a tarefa for só picar cebola (cálculo pesado), um chef só tem um limite físico.
- **Multiprocessing** é contratar **Vários Chefs com suas próprias bancadas**: cada um pica sua cebola em sua própria tábua. O trabalho é dividido de verdade. Se você tem 4 CPUs, é como ter 4 chefs trabalhando em paralelo absoluto.

### Desafio de Aplicação CLI: "O Simulador de Download Paralelo"
Use o módulo `threading` para criar uma função que simule o download de um arquivo (use `time.sleep(2)` para simular a espera). Dispare 3 threads simultâneas e veja que elas terminam quase ao mesmo tempo, em vez de levar 6 segundos no total.

### Gabarito do Desafio
```python
import threading
import time

def baixar_arquivo(nome):
    print(f"Iniciando download de {nome}...")
    time.sleep(2) # Simulando espera de internet
    print(f"Download de {nome} CONCLUÍDO!")

# Criando as threads
t1 = threading.Thread(target=baixar_arquivo, args=("Foto.jpg",))
t2 = threading.Thread(target=baixar_arquivo, args=("Video.mp4",))
t3 = threading.Thread(target=baixar_arquivo, args=("Documento.pdf",))

# Iniciando as tarefas em paralelo
inicio = time.time()
t1.start()
t2.start()
t3.start()

# Esperando todas terminarem para seguir com o programa principal
t1.join()
t2.join()
t3.join()
fim = time.time()

print(f"Tempo total decorrido: {fim - inicio:.2f} segundos.")
```

### Quiz de Fixação
1. Qual o nome da trava do Python que impede Threads de rodarem códigos CPU-bound em paralelo real?
   > **Resposta:** GIL (Global Interpreter Lock).
2. Se eu preciso processar um vídeo em 4K e aplicar filtros pesados, devo usar Threads ou Multiprocessing?
   > **Resposta:** Multiprocessing (para usar múltiplos núcleos da CPU).
3. O que faz o método `.join()` em uma Thread?
   > **Resposta:** Faz com que o programa principal espere aquela Thread terminar antes de continuar a execução.

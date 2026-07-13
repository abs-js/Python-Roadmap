# Capítulo 72: Threading Lock – O Bastão de Revezamento

### Teoria Sem Enrolação
Vimos que Threads rodam em paralelo, mas e se duas threads tentarem mudar a mesma variável ao mesmo tempo? Isso gera uma **Race Condition** (Condição de Corrida), onde o resultado final fica imprevisível e bugado.
Para resolver isso, usamos o **`threading.Lock`**.
- Um Lock tem dois estados: **adquirido** ou **liberado**.
- Quando uma thread dá um `acquire()`, nenhuma outra thread consegue passar por ali até que a primeira dê o `release()`.
- A forma mais segura de usar é com o `with meu_lock:`, que garante a liberação automática.

### A Grande Analogia
Imagine um **Banheiro Químico em um Evento**.
Não importa se há 1.000 pessoas (threads) querendo usar. O **Cadeado** (Lock) garante que apenas uma pessoa por vez entre. 
Se a porta está trancada (Lock adquirido), as outras pessoas precisam esperar na fila. Assim que a pessoa sai e destranca a porta (Lock liberado), a próxima da fila pode entrar. Sem o cadeado, duas pessoas tentariam entrar ao mesmo tempo e o resultado seria um desastre (Race Condition).

### Desafio de Aplicação CLI: "O Contador Compartilhado"
Crie uma variável `saldo = 0` e um `lock`. 
1. Crie uma função que rode 100.000 vezes um incremento de `+1` no saldo.
2. Dispare 2 threads para rodar essa função simultaneamente.
3. Use o `lock` para garantir que o saldo final seja exatamente 200.000 (sem o lock, o valor provavelmente será menor devido às colisões).

### Gabarito do Desafio
```python
import threading

saldo = 0
cadeado = threading.Lock()

def depositar():
    global saldo
    for _ in range(100000):
        # Garantindo que apenas uma thread mexa no saldo por vez
        with cadeado:
            saldo += 1

t1 = threading.Thread(target=depositar)
t2 = threading.Thread(target=depositar)

t1.start()
t2.start()
t1.join()
t2.join()

print(f"Saldo final: {saldo}")
```

### Quiz de Fixação
1. O que acontece se uma thread der um `acquire()` e esquecer de dar o `release()`?
   > **Resposta:** Ocorre um **Deadlock**: todas as outras threads que precisam do lock ficarão paradas para sempre.
2. Por que usar `with cadeado:` é melhor que chamar os métodos manualmente?
   > **Resposta:** Porque o `with` garante que o lock seja liberado mesmo se ocorrer um erro/exceção dentro do bloco.
3. O Lock resolve o problema de performance do Python (GIL)?
   > **Resposta:** Não, o Lock serve apenas para garantir a integridade dos dados quando múltiplas threads acessam o mesmo recurso.

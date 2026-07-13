# Capítulo 48: Garbage Collection (Coletor de Lixo) – O Zelador de Memória

### Teoria Sem Enrolação
O Python gerencia a memória para você através de duas técnicas:
1. **Contagem de Referências:** Cada objeto guarda um número de quantos nomes apontam para ele. Se chegar a 0, o Python apaga o objeto da memória imediatamente.
2. **Garbage Collector (GC):** Focado em resolver "Referências Cíclicas" (quando o Objeto A aponta para o B e o B aponta para o A, mas ninguém mais na terra usa eles). O GC roda periodicamente para encontrar esses "zumbis" e limpá-los.

### A Grande Analogia
Imagine uma **Biblioteca Pública**.
- A **Contagem de Referência** é uma ficha atrás do livro: cada vez que alguém aluga o livro, a contagem aumenta. Quando todos devolvem, a bibliotecária percebe que o livro está parado há décadas e não tem mais leitores, então ela o joga fora para ganhar espaço na prateleira.
- O **GC** é um **Detetive**: ele entra no arquivo morto e percebe que o João disse que pegou o livro da Maria, e a Maria disse que pegou o livro do João, mas os dois já nem moram mais na cidade. Eles estão travando o sistema entre si. O detetive limpa os dois de uma vez.

### Desafio de Aplicação CLI: "Forçando a Limpeza"
O Python permite interagir com o coletor através do módulo `gc`. 
1. Crie uma classe simples que imprime "Tchau!" quando é destruída (use o método mágico `__del__`).
2. Crie uma referência cíclica (objeto A aponta para B, B aponta para A).
3. Delete os nomes originais e veja que o "Tchau!" não aparece.
4. Chame `gc.collect()` manualmente para forçar a limpeza e veja o que acontece.

### Gabarito do Desafio
```python
import gc

class Objeto:
    def __init__(self, nome):
        self.nome = nome
        self.amigo = None
    def __del__(self):
        print(f"Objeto {self.nome} foi limpo da memória!")

# Criando o ciclo
a = Objeto("A")
b = Objeto("B")
a.amigo = b
b.amigo = a

# Removendo as referências principais
del a
del b
print("Nomes 'a' e 'b' deletados, mas o ciclo continua na memória...")

# Forçando a coleta de lixo
print(f"Itens coletados: {gc.collect()}")
```

### Quiz de Fixação
1. Qual o principal mecanismo de gerenciamento de memória do Python?
   > **Resposta:** Contagem de Referências (Reference Counting).
2. O que é uma referência cíclica?
   > **Resposta:** Quando dois ou mais objetos referenciam uns aos outros de modo que a contagem de referência nunca chegue a zero, mesmo que o resto do programa não os use mais.
3. Qual o nome do método mágico chamado quando um objeto está prestes a ser destruído?
   > **Resposta:** `__del__`.

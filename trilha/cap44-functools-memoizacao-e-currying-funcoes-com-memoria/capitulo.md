# Capítulo 44: Functools – Memoização e Currying (Funções com Memória)

### Teoria Sem Enrolação
O módulo **`functools`** serve para manipular ou estender as capacidades de outras funções.
- **`@lru_cache`**: Talvez o decorador mais útil do Python. Ele guarda o resultado de uma função na memória (cache). Se você chamar a função com o mesmo parâmetro de novo, ela não recalcula; ela entrega o resultado guardado instantaneamente.
- **`partial()`**: Permite que você "pré-preencha" alguns argumentos de uma função e crie uma nova função mais simples a partir dela.

### A Grande Analogia
Imagine que você é um **Bibliotecário**. 
- O **`lru_cache`** é a sua **Mesa de Favoritos**: em vez de ir até a estante lá no fundo toda vez que alguém pede o mesmo livro de Geografia, você deixa o livro em cima da mesa. Se pedirem de novo, você entrega em 1 segundo. Se a mesa encher, você joga fora o livro que ninguém pede há mais tempo (Least Recently Used).
- O **`partial`** é como um **Carimbo Personalizado**: em vez de escrever "Aprovado por: Dr. Silva, em 2024" em 1.000 papéis, você cria um carimbo que já tem o nome e a data. Agora você só precisa fazer o movimento de carimbar o nome do aluno.

### Desafio de Aplicação CLI: "O Super Fibonacci com Cache"
O cálculo de Fibonacci de forma recursiva é lento porque recalcula os mesmos números milhares de vezes.
1. Crie uma função recursiva `fibonacci(n)`.
2. Use o decorador `@lru_cache` do `functools`.
3. Compare a velocidade de calcular `fibonacci(40)` com e sem o decorador.

### Gabarito do Desafio
```python
from functools import lru_cache
import time

@lru_cache(maxsize=None)
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

inicio = time.time()
resultado = fibonacci(40)
fim = time.time()

print(f"Fibonacci(40) = {resultado}")
print(f"Tempo com cache: {fim - inicio:.6f} segundos")
```

### Quiz de Fixação
1. Qual o principal benefício de usar `@lru_cache` em funções recursivas?
   > **Resposta:** Evitar o recalculo de valores já processados, transformando um tempo de execução exponencial em linear.
2. O que o parâmetro `maxsize` faz no `@lru_cache`?
   > **Resposta:** Define quantos resultados diferentes a função pode guardar antes de começar a apagar os mais antigos.
3. Qual a utilidade da função `partial`?
   > **Resposta:** Fixar alguns argumentos de uma função, gerando uma nova função que requer menos parâmetros para ser chamada.

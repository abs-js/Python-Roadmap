# Capítulo 8: Estruturas de Repetição (For) – A Automação de Tarefas

### Teoria Sem Enrolação
O `for` é usado quando você quer repetir uma ação para cada item de uma coleção (lista, tupla, string) ou um número determinado de vezes.
- **A sintaxe:** `for item in colecao:`
- **A função `range(inicio, fim)`:** Gera uma sequência de números. Importante: o Python para **antes** do número final. `range(1, 5)` gera 1, 2, 3, 4.

### A Grande Analogia
Imagine que você é um **Grampeador Humano**. Você tem uma pilha de 50 processos para grampear.
O seu cérebro executa um `for`:
"Para **cada processo** na **pilha**, eu vou: 1. Pegar o papel, 2. Colocar o grampo, 3. Colocar na mesa de saída."
Você não questiona se deve continuar; você simplesmente percorre a pilha até que o último processo seja grampeado.

### Desafio de Aplicação CLI: "A Tabuada Inteligente"
Peça ao usuário um número inteiro. Use um laço `for` e a função `range()` para imprimir a tabuada desse número do 1 ao 10.

### Gabarito do Desafio
```python
numero = int(input("Você quer a tabuada de qual número? "))

print(f"--- TABUADA DO {numero} ---")

# O range vai de 1 até 11 para incluir o 10
for i in range(1, 11):
    resultado = numero * i
    print(f"{numero} x {i} = {resultado}")

print("-----------------------")
```

### Quiz de Fixação
1. Como o `for` sabe que deve parar de executar?
   > **Resposta:** Ele para automaticamente quando percorre todos os itens da coleção ou o limite do `range`.
2. O que o comando `range(5)` produz?
   > **Resposta:** Uma sequência de 0 a 4 (cinco números no total).
3. Posso usar um `for` para percorrer as letras de uma palavra (string)?
   > **Resposta:** Sim, o Python tratará cada letra como um item da repetição.

# Capítulo 29: Recursão – A Função Espelho

### Teoria Sem Enrolação
Recursão é quando uma função chama a si mesma para resolver um problema. Para não entrar em um loop infinito, toda função recursiva precisa de dois componentes:
1. **Caso Base:** A condição de parada (quando a função para de se chamar).
2. **Caso Recursivo:** A parte onde a função chama a si mesma com um dado menor ou simplificado, aproximando-se do caso base.

### A Grande Analogia
Imagine que você está no topo de uma **Escada no Escuro** e quer saber quantos degraus existem. 
Você não consegue ver o chão. Então você desce **um degrau** e pergunta para você mesmo: "Quantos degraus faltam daqui?". Você repete isso até que o seu pé toque o chão (Caso Base). Quando toca o chão, você sabe que faltam 0. Aí você volta subindo e somando: "0 + 1 lá embaixo, + 1 aqui...". Quando chegar no topo, você terá o total.

### Desafio de Aplicação CLI: "O Cálculo de Fatorial"
O fatorial de um número (n!) é ele multiplicado por todos os seus antecessores até 1. 
Ex: 5! = 5 * 4 * 3 * 2 * 1 = 120.
Crie uma função recursiva `fatorial(n)` que calcule esse valor.

### Gabarito do Desafio
```python
def fatorial(n: int) -> int:
    # Caso Base: o fatorial de 1 ou 0 é 1
    if n <= 1:
        return 1
    # Caso Recursivo: n * fatorial do seu antecessor
    else:
        return n * fatorial(n - 1)

numero = int(input("Digite um número para ver o fatorial: "))
print(f"O fatorial de {numero} é {fatorial(numero)}")
```

### Quiz de Fixação
1. O que acontece se uma função recursiva não tiver um Caso Base?
   > **Resposta:** Ocorre um erro de "RecursionError" (estouro da pilha), pois a função se chamará infinitamente.
2. Qual a principal vantagem visual da recursão?
   > **Resposta:** Ela torna o código mais limpo e elegante para problemas matemáticos ou estruturas de dados em árvore.
3. Posso resolver qualquer problema recursivo usando um loop `while` ou `for`?
   > **Resposta:** Sim, qualquer algoritmo recursivo pode ser transformado em iterativo (loops).

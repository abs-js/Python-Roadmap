# Capítulo 4: Operadores Aritméticos e Lógicos - As Engrenagens do Pensamento

### Teoria Sem Enrolação
Para o Python, tudo se resume a processar dados. Para isso, usamos dois tipos de ferramentas:
1.  **Operadores Matemáticos:** Além do básico (`+`, `-`, `*`, `/`), temos três que são essenciais:
    *   `//` (Divisão Inteira): Divide e descarta o que vem depois da vírgula.
    *   `%` (Módulo): Pega apenas o **resto** da divisão (muito usado para saber se um número é par ou ímpar).
    *   `**` (Exponenciação): Eleva um número a outro.
2.  **Operadores Lógicos (and, or, not):** Usados para combinar perguntas.
    *   `and`: Só é verdade se **tudo** for verdade.
    *   `or`: É verdade se **pelo menos um** for verdade.
    *   `not`: Inverte o valor (o que é True vira False).

### A Grande Analogia
Pense nos operadores como **utensílios de cozinha**. 
Os matemáticos são as facas e batedeiras que transformam os ingredientes. Já os operadores lógicos são os **critérios de uma receita**. 
- Exemplo do `and`: "Para fazer o bolo, preciso de farinha **E** ovos". Se faltar um, não tem bolo.
- Exemplo do `or`: "Para beber algo, pode ser água **OU** suco". Se tiver qualquer um dos dois, você mata a sede.

### Desafio de Aplicação CLI: "O Analisador de Números Mágico"
Crie um programa que peça ao usuário um número inteiro. O programa deve exibir:
1. O número elevado ao quadrado.
2. O resto da divisão desse número por 2.
3. Se o número é maior que 10 **E** menor que 50 (exibindo True ou False).

### Gabarito do Desafio
```python
# Entrada do número
num = int(input("Digite um número inteiro: "))

# Processamento
quadrado = num ** 2
resto = num % 2
intervalo = num > 10 and num < 50

# Saída
print(f"O quadrado de {num} é: {quadrado}")
print(f"O resto da divisão por 2 (0=par, 1=ímpar) é: {resto}")
print(f"O número está entre 10 e 50? {intervalo}")
```

### Quiz de Fixação
1. Qual o resultado de `10 % 3`?
   > **Resposta:** 1. (Pois 10 dividido por 3 é 3, e sobra 1).
2. Se `tem_dinheiro = True` e `tem_tempo = False`, qual o resultado de `tem_dinheiro or tem_tempo`?
   > **Resposta:** True. (No `or`, basta um ser verdadeiro).
3. Como se escreve "2 elevado a 3" em Python?
   > **Resposta:** `2 ** 3`.

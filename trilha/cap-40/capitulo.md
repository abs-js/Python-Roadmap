# Capítulo 40: Walrus Operator (`:=`) — O Atribuidor Multitarefa

### Teoria Sem Enrolação
Introduzido no Python 3.8, o **Walrus Operator** (operador morsa, devido aos olhos e presas `:=`) permite que você atribua um valor a uma variável **dentro** de uma expressão. 
Normalmente, você faria: 
1. Calcula algo.
2. Guarda na variável.
3. Usa a variável no `if` ou `while`.
Com o Walrus, você faz os três passos de uma vez só. Isso torna o código mais curto e evita repetir chamadas de funções pesadas.

### A Grande Analogia
Imagine que você é um **Pescador**. 
O jeito tradicional é: você puxa o peixe da água, coloca ele no balde e, só depois, olha para o balde para ver se o peixe é grande o suficiente para levar para casa.
Com o **Walrus Operator**, você tem uma **Balança Acoplada ao Anzol**: no exato momento em que você fisga o peixe (expressão), você já vê o peso e decide se ele vai para o balde ou não. Você economiza o movimento de "colocar no balde antes de checar".

### Desafio de Aplicação CLI: "O Coletor de Notas Inteligente"
Crie um programa que peça nomes de alunos em um loop `while`. 
1. O loop deve continuar enquanto o usuário não digitar "fim".
2. Use o Walrus Operator para capturar o input e testar a condição de parada na mesma linha do `while`.
3. Vá guardando os nomes em uma lista e exiba-os ao final.

### Gabarito do Desafio
```python
nomes = []

# O input e a verificação acontecem na mesma linha!
while (nome := input("Digite um nome (ou 'fim' para sair): ")) != "fim":
    nomes.append(nome)

print(f"Lista de alunos cadastrados: {nomes}")
```

### Quiz de Fixação
1. Por que o operador `:=` é chamado de "Walrus" (Morsa)?
   > **Resposta:** Porque, se você virar a cabeça de lado, os dois pontos `:` parecem olhos e o igual `=` parece as presas de uma morsa.
2. Onde o Walrus Operator é mais comumente utilizado?
   > **Resposta:** Em condições de loops `while` e em verificações de `if` que envolvem cálculos ou funções.
3. O Walrus Operator funciona em versões de Python anteriores à 3.8?
   > **Resposta:** Não, ele é uma adição relativamente recente da linguagem.

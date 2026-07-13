# Capítulo 11: List Comprehension – A Linha de Produção Expressa

### Teoria Sem Enrolação
List Comprehension é uma forma "ninja" do Python de criar novas listas a partir de listas existentes de forma muito rápida, em apenas uma linha. 
A estrutura básica é: `[o_que_fazer for item in lista_antiga if condicao]`.
Isso substitui 4 ou 5 linhas de um `for` tradicional por uma única linha elegante.

### A Grande Analogia
Imagine uma **Esteira de Fábrica de Laranjas**. 
O jeito antigo (`for` tradicional) seria: pegar uma laranja, olhar se ela está podre, se estiver boa, colocar na caixa, repetir. 
Com **List Comprehension**, você instala um **Filtro Mágico** na esteira. Você diz: "Quero uma caixa nova contendo apenas o suco de todas as laranjas que forem grandes". O processo acontece em um fluxo único e contínuo.

### Desafio de Aplicação CLI: "O Filtro de Notas Fiscais"
Você tem uma lista de valores de vendas: `[100, 250, 50, 500, 120, 80]`. 
Crie uma nova lista chamada `vendas_premium` usando List Comprehension que contenha apenas as vendas acima de 150 reais e aplique um bônus de 10% (multiplique por 1.1) em cada uma delas.

### Gabarito do Desafio
```python
vendas = [100, 250, 50, 500, 120, 80]

# List Comprehension com lógica: (valor * 1.1) é a ação | (for v in vendas) é o loop | (if v > 150) é o filtro
vendas_premium = [v * 1.1 for v in vendas if v > 150]

print(f"Vendas originais: {vendas}")
print(f"Vendas Premium com bônus: {vendas_premium}")
```

### Quiz de Fixação
1. Qual o símbolo que delimita uma List Comprehension?
   > **Resposta:** Colchetes `[ ]`.
2. A parte do `if` é obrigatória em toda List Comprehension?
   > **Resposta:** Não, ela é opcional e serve para filtrar os itens.
3. List Comprehension é geralmente mais lenta ou mais rápida que um loop `for` tradicional?
   > **Resposta:** Geralmente é mais rápida e performática em Python.

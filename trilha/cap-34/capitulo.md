# Capítulo 34: Comprehensions de Dicionários e Conjuntos — A Refinaria de Dados

### Teoria Sem Enrolação
Você já domina as *List Comprehensions*, mas o Python permite aplicar a mesma elegância para criar **Dicionários** e **Sets** (Conjuntos) em uma única linha.
- **Dict Comprehension:** `{chave: valor for item in colecao if condicao}`. Excelente para transformar listas de tuplas em dicionários ou inverter mapeamentos.
- **Set Comprehension:** `{item for item in colecao if condicao}`. Funciona como a de lista, mas garante que o resultado final contenha apenas elementos únicos (sem duplicatas).

### A Grande Analogia
Imagine que você tem uma **Caixa de Ferramentas** bagunçada.
- A **Dict Comprehension** é como uma etiqueta inteligente: você passa a mão na caixa e diz: "Para cada ferramenta, use o nome dela como etiqueta e o peso dela como valor". Em um segundo, tudo está catalogado.
- A **Set Comprehension** é como um **Filtro de Peneira**: você joga um monte de parafusos (alguns repetidos) na peneira. Ela sacode tudo e te entrega apenas **um exemplar de cada tipo**, descartando as cópias desnecessárias.

### Desafio de Aplicação CLI: "O Indexador de Preços"
Você tem uma lista de nomes de produtos: `['teclado', 'mouse', 'monitor']` e outra lista de preços: `[150, 80, 900]`.
1. Use a função `zip()` e uma **Dict Comprehension** para criar um dicionário que ligue o nome ao preço.
2. Crie um **Set** a partir da lista `['maçã', 'banana', 'maçã', 'laranja', 'banana']` para descobrir quais são as frutas únicas disponíveis, usando Set Comprehension.

### Gabarito do Desafio
```python
produtos = ['teclado', 'mouse', 'monitor']
precos = [150, 80, 900]

# Criando o dicionário de forma ultra rápida
# zip(produtos, precos) cria pares como ('teclado', 150)
tabela_precos = {nome: preco for nome, preco in zip(produtos, precos)}
print(f"Dicionário de Preços: {tabela_precos}")

# Extraindo itens únicos
frutas_repetidas = ['maçã', 'banana', 'maçã', 'laranja', 'banana']
frutas_unicas = {fruta.upper() for fruta in frutas_repetidas}
print(f"Frutas Únicas (em maiúsculo): {frutas_unicas}")
```

### Quiz de Fixação
1. Qual a principal diferença visual na sintaxe entre uma List e uma Set Comprehension?
   > **Resposta:** A List usa colchetes `[]` e a Set usa chaves `{}`.
2. Como transformamos uma List Comprehension em um Dict Comprehension?
   > **Resposta:** Incluindo a definição de par `chave: valor` antes do `for`.
3. O que acontece se uma Dict Comprehension encontrar duas chaves iguais durante o loop?
   > **Resposta:** O último valor processado sobrescreverá o anterior para aquela chave.

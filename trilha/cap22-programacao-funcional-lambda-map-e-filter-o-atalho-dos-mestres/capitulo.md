# Capítulo 22: Programação Funcional (Lambda, Map e Filter) – O Atalho dos Mestres

### Teoria Sem Enrolação
Às vezes, criar uma função inteira com `def` para uma tarefa simples de uma única linha é um exagero. O Python permite a **Programação Funcional** para processar coleções de dados de forma elegante:
- **Lambda:** São funções anônimas (sem nome). Elas só podem ter uma única expressão. Sintaxe: `lambda x: x * 2`.
- **Map:** Pega uma função e a aplica a **todos** os itens de uma lista. 
- **Filter:** Pega uma função que retorna verdadeiro ou falso e "filtra" a lista, deixando passar apenas o que interessa.

### A Grande Analogia
Imagine que você é o dono de uma **Fábrica de Camisetas**.
- O **Map** é a sua **Máquina de Estampa**: você coloca 100 camisetas brancas de um lado e ela entrega 100 camisetas estampadas do outro. Ela transformou cada item da lista original.
- O **Filter** é o seu **Controle de Qualidade**: você passa todas as camisetas prontas, mas a máquina só deixa seguir para a caixa de vendas aquelas que não têm furos (os itens que atendem à condição).
- A **Lambda** é aquele **Adesivo Rápido** que você cola na máquina só para um lote específico, sem precisar reprogramar toda a fábrica.

### Desafio de Aplicação CLI: "O Sistema de Promoção Relâmpago"
Você tem uma lista de preços de produtos: `[1200, 50, 800, 20, 1500, 300]`.
Crie um programa que use Programação Funcional para:
1. Filtrar apenas os produtos "Caros" (acima de R$ 500,00).
2. Aplicar um desconto de 20% em todos esses produtos caros.
3. Exibir a lista final de preços promocionais.

### Gabarito do Desafio
```python
precos = [1200, 50, 800, 20, 1500, 300]

# 1. Filtrando os caros (Filter)
caros = filter(lambda p: p > 500, precos)

# 2. Aplicando 20% de desconto (Map)
promocionais = map(lambda p: p * 0.8, caros)

# Convertendo o resultado final para uma lista para poder imprimir
lista_final = list(promocionais)

print("Preços originais:", precos)
print("Novos preços (apenas dos produtos acima de 500 com 20% OFF):")
print(lista_final)
```

### Quiz de Fixação
1. Qual a principal limitação de uma função `lambda`?
   > **Resposta:** Ela só pode conter uma única expressão (uma única linha de lógica).
2. O que a função `map` retorna por padrão em Python 3?
   > **Resposta:** Um objeto "map" (um iterator). Por isso, precisamos usar `list()` para ver os resultados.
3. Qual a diferença entre `map` e `filter`?
   > **Resposta:** O `map` transforma os elementos; o `filter` seleciona elementos sem alterá-los.

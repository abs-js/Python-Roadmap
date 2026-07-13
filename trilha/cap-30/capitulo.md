# Capítulo 30: Módulo Collections – Ferramentas de Elite

### Teoria Sem Enrolação
O Python tem listas e dicionários, mas o módulo nativo `collections` traz estruturas de dados turbinadas para problemas específicos:
- **`Counter`**: Conta automaticamente a frequência de itens em uma lista.
- **`deque`**: Uma lista de "dupla extremidade" otimizada para adicionar ou remover itens tanto do início quanto do fim (muito rápida para filas).
- **`namedtuple`**: Cria uma "mini-classe" rápida que se comporta como uma tupla, mas permite acessar dados por nome (ex: `ponto.x`) em vez de índice (`ponto[0]`).

### A Grande Analogia
Imagine que você é um **Marceneiro**. 
Uma Lista comum é o seu **Martelo**: serve para quase tudo. 
Mas em certos momentos, você precisa de uma **Pistola de Pregos Eletrônica** (`Counter`): ela faz em 1 segundo o que você levaria minutos fazendo manualmente. Ou você precisa de um **Cinto de Ferramentas Magnético** (`deque`), onde você pega e guarda ferramentas de qualquer lado com agilidade extrema. O módulo `collections` é a sua **Maleta Especialista**.

### Desafio de Aplicação CLI: "Analisador de Frequência de Texto"
Crie um programa que receba uma frase do usuário e, usando o `Counter`, exiba quais foram as 3 letras que mais apareceram e quantas vezes cada uma ocorreu.

### Gabarito do Desafio
```python
from collections import Counter

frase = input("Digite uma frase para análise: ").lower()
# Removemos espaços para focar apenas nas letras
letras = [char for char in frase if char.isalpha()]

# O Counter faz toda a mágica da contagem
contagem = Counter(letras)

# O método most_common(n) retorna os top 'n' itens
top_3 = contagem.most_common(3)

print("\n--- RANKING DE LETRAS ---")
for letra, qtd in top_3:
    print(f"Letra '{letra}': {qtd} vezes")
```

### Quiz de Fixação
1. Qual estrutura do módulo `collections` é ideal para contar votos em uma eleição?
   > **Resposta:** `Counter`.
2. Por que usar `deque` em vez de uma `list` comum para remover o primeiro item de uma coleção gigante?
   > **Resposta:** Porque o `deque` é otimizado para isso; em listas comuns, o Python precisa "reindexar" todos os outros itens, o que é lento.
3. O que uma `namedtuple` oferece a mais que uma tupla normal?
   > **Resposta:** Legibilidade, permitindo acessar os valores por nomes de atributos.

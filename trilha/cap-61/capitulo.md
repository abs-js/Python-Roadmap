# Capítulo 61: DefaultDict – O Dicionário que Nunca Diz "Não"

### Teoria Sem Enrolação
Quando você tenta acessar uma chave que não existe em um dicionário comum, o Python lança um erro de chave (`KeyError`). O **`defaultdict`** (do módulo `collections`) resolve isso. 
Ao criá-lo, você passa uma "fábrica" de funções (como `int`, `list` ou `set`). Se você tentar acessar ou modificar uma chave inexistente, o `defaultdict` cria essa chave na hora com um valor padrão automaticamente. Isso elimina a necessidade de ficar verificando `if chave in dicionario` o tempo todo.

### A Grande Analogia
Imagine que você é um **Bibliotecário** organizando devoluções. 
- No **Dicionário Comum**, se um aluno chega com um livro de "Astronomia" e você ainda não tem uma prateleira de Astronomia montada, você entra em pânico e diz que não pode aceitar o livro (Erro). Você teria que parar, construir a prateleira e depois guardar o livro.
- No **DefaultDict**, você tem um **Ajudante Mágico**. Assim que o aluno diz "Astronomia", o ajudante num piscar de olhos constrói uma prateleira vazia para você. Você só se preocupa em colocar o livro lá dentro. O ajudante garante que a estrutura sempre exista no momento em que você precisa dela.

### Desafio de Aplicação CLI: "O Agrupador de Palavras por Tamanho"
Crie um programa que receba várias palavras do usuário. 
1. Use um `defaultdict(list)` para agrupar as palavras de acordo com a quantidade de letras que elas possuem.
2. Exemplo: Se o usuário digitar "oi", "casa", "pé", o dicionário deve ficar: `{2: ['oi', 'pé'], 4: ['casa']}`.
3. Imprima o resultado final de forma organizada.

### Gabarito do Desafio
```python
from collections import defaultdict

# Criamos o dicionário onde o valor padrão é uma LISTA vazia
palavras_por_tamanho = defaultdict(list)

print("Digite palavras (digite 'sair' para parar):")
while True:
    entrada = input("> ").strip()
    if entrada.lower() == 'sair':
        break
    
    tamanho = len(entrada)
    # Não precisamos verificar se a chave existe! 
    # O defaultdict cria a lista vazia se for a primeira vez que vemos esse tamanho.
    palavras_por_tamanho[tamanho].append(entrada)

print("\n--- RESULTADO ---")
for tamanho, lista in sorted(palavras_por_tamanho.items()):
    print(f"Palavras com {tamanho} letras: {lista}")
```

### Quiz de Fixação
1. O que acontece se eu tentar acessar `meu_defaultdict['chave_inexistente']`?
   > **Resposta:** O Python cria a chave automaticamente com o valor padrão definido (ex: 0 para `int`, `[]` para `list`).
2. Qual comando importamos para usar essa ferramenta?
   > **Resposta:** `from collections import defaultdict`.
3. Posso usar uma função própria (ex: `lambda: "Vazio"`) como valor padrão?
   > **Resposta:** Sim, qualquer função que retorne um valor pode ser usada como a "fábrica" de valores padrão.

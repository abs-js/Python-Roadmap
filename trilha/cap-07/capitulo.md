# Capítulo 7: Tuplas, Sets e Dicionários – Além das Listas

### Teoria Sem Enrolação
Nem toda coleção de dados deve ser igual. O Python oferece três ferramentas especializadas:
1.  **Tuplas `(valor1, valor2)`:** São como listas, mas **imutáveis**. Uma vez criadas, você não pode adicionar, remover ou alterar itens. São mais rápidas e seguras para dados que não devem mudar (como coordenadas de um GPS ou meses do ano).
2.  **Sets `{valor1, valor2}`:** Conjuntos que **não permitem itens duplicados** e não possuem ordem. Úteis para filtrar duplicatas e fazer operações matemáticas de conjuntos (união, intersecção).
3.  **Dicionários `{"chave": "valor"}`:** Funcionam como uma base de dados. Em vez de acessar por um índice numérico (0, 1, 2...), você acessa por uma **chave** (um nome). 

### A Grande Analogia
Imagine que você está organizando um escritório:
-   A **Tupla** é como um **RG ou CPF**: uma vez emitido, os dados ali são fixos. Tentar mudar o número do seu RG é ilegal no mundo real e gera erro no Python.
-   O **Set** é uma **caixa de figurinhas repetidas**: se você tem três figurinhas do Neymar e joga todas lá dentro, a caixa entende que você só tem "uma unidade do tipo Neymar".
-   O **Dicionário** é a **Agenda de Contatos**: você não procura o telefone do seu amigo pela posição 50 da agenda, você procura pela "chave" (o nome dele) para encontrar o "valor" (o número do telefone).

### Desafio de Aplicação CLI: "O Tradutor de Emojis"
Crie um programa que funcione como um dicionário de tradução.
1. Crie um dicionário onde as chaves são códigos (ex: ":)", ":(", "S2") e os valores são as descrições (ex: "Feliz", "Triste", "Coração").
2. Pergunte ao usuário qual código ele quer traduzir.
3. Se o código existir, mostre a tradução. Se não existir, avise que o termo é desconhecido.

### Gabarito do Desafio
```python
# Criando o dicionário (nossa base de conhecimento)
dicionario_emoji = {
    ":)": "Feliz / Sorridente",
    ":(": "Triste / Chateado",
    "S2": "Coração / Amor",
    "??": "Confuso"
}

# Entrada do usuário
termo = input("Digite um emoji para traduzir (Ex: :), S2, ??): ")

# Verificando e exibindo (usando o método .get para evitar erros)
traducao = dicionario_emoji.get(termo, "Emoji não encontrado no sistema.")
print(f"Resultado: {traducao}")
```

### Quiz de Fixação
1. Qual a principal diferença entre uma Lista e uma Tupla?
   > **Resposta:** A lista pode ser alterada (mutável), enquanto a tupla é fixa (imutável).
2. Se eu criar o set `meu_set = {1, 2, 2, 3}`, qual será o conteúdo final dele?
   > **Resposta:** `{1, 2, 3}` (o 2 duplicado é removido automaticamente).
3. Como acessamos um valor dentro de um dicionário?
   > **Resposta:** Usando a chave correspondente entre colchetes, ex: `dicionario["chave"]`.

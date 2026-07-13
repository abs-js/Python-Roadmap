# Capítulo 1: Python e as Etiquetas Magnéticas (Variáveis)

### Teoria Sem Enrolação
Imagine que o computador é uma memória gigantesca, cheia de gavetas vazias. Quando você cria uma **variável**, você não está apenas "guardando" algo; você está pegando uma dessas gavetas e colando uma **etiqueta** nela para saber o que tem dentro.

No Python, criar uma variável é tão simples quanto escrever `nome_da_variavel = valor`. 
- O `=` não significa "igual" (como na matemática), mas sim **atribuição**. Você está dizendo: "Ei, computador, pegue este valor e coloque dentro desta etiqueta".
- **Regras de Ouro (PEP 8):** Nomes de variáveis devem ser em letras minúsculas e usar o `_` (underscore) para separar palavras (ex: `salario_mensal`). Isso é o que chamamos de *snake_case*.

### A Grande Analogia
Imagine que você é o gerente de um **Almoxarifado Gigante**. Milhares de caixas chegam por segundo. Se você apenas jogar as coisas no chão, nunca mais as achará. O que você faz? Você pega uma caixa, coloca um item (como uma "Chave de Fenda") e cola um adesivo escrito "Ferramenta_01". 
A **variável** é o adesivo. O **valor** é o que está dentro da caixa. Se amanhã você tirar a chave de fenda e colocar um martelo, a etiqueta continua lá, mas o conteúdo mudou.

### Desafio de Aplicação CLI: "O Arquivista Digital"
Crie um programa que armazene as informações de um livro: o título, o autor, o ano de publicação e se ele está disponível para empréstimo. Você deve imprimir essas informações de forma organizada no console.

### Gabarito do Desafio
```python
# Definindo as variáveis (as etiquetas do nosso arquivo)
titulo_livro = "O Guia do Mochileiro das Galáxias"
autor = "Douglas Adams"
ano_publicacao = 1979
disponivel_para_emprestimo = True # Valor Booleano (Verdadeiro)

# Exibindo os dados de forma organizada
print("--- FICHA DO LIVRO ---")
print("Título:", titulo_livro)
print("Autor:", autor)
print("Ano:", ano_publicacao)
print("Disponível:", disponivel_para_emprestimo)
print("-----------------------")
```

### Quiz de Fixação
1. Qual o nome do padrão de escrita de variáveis em Python onde usamos underline? 
   > **Resposta:** snake_case.
2. O que acontece se começarmos o nome de uma variável com um número (ex: `1nome`)?
   > **Resposta:** O Python retornará um erro de sintaxe, pois variáveis não podem começar com números.
3. O operador `=` serve para comparar se dois valores são iguais?
   > **Resposta:** Não, ele serve para atribuir (guardar) um valor a uma variável.

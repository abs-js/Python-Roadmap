# Capítulo 28: Type Hinting (Tipagem de Dados) – O Código Autodocumentado

### Teoria Sem Enrolação
O Python é uma linguagem de tipagem dinâmica (você não precisa dizer que uma variável é `int` ou `str`), mas em projetos grandes isso pode gerar confusão. O **Type Hinting** permite que você indique o tipo esperado de variáveis, parâmetros de função e retornos usando a sintaxe `: tipo` e `-> tipo`. 
- Isso não impede o Python de rodar se o tipo for diferente (é apenas uma "dica"), mas ferramentas como o **MyPy** e o VS Code usam isso para avisar erros antes mesmo de você executar o código.

### A Grande Analogia
Imagine que você está organizando uma **Mudança de Casa**. 
Você pode simplesmente jogar tudo em caixas pardas. O caminhão vai levar (o Python vai rodar). Mas quando você chegar na casa nova, terá que abrir todas para saber o que tem dentro. 
O **Type Hinting** é o ato de escrever com um pincel atômico na caixa: **"LIVROS"** ou **"FRÁGIL: TAÇAS"**. Se você colocar um martelo dentro da caixa de taças, ninguém vai te prender, mas quem ler o rótulo (seu editor de código ou outro programador) vai te avisar: "Ei, isso não devia estar aqui!".

### Desafio de Aplicação CLI: "O Sistema de Cadastro Tipado"
Crie uma função chamada `formatar_usuario` que recebe:
1. `nome` (deve ser string).
2. `idade` (deve ser inteiro).
3. `altura` (deve ser float).
A função deve retornar uma string formatada. Use Type Hints para todos os parâmetros e para o retorno da função.

### Gabarito do Desafio
```python
# Usando Type Hints para clareza total
def formatar_usuario(nome: str, idade: int, altura: float) -> str:
    return f"Usuário: {nome} | {idade} anos | Altura: {altura}m"

# Testando
nome_input: str = "Arthur"
idade_input: int = 25
altura_input: float = 1.83

print(formatar_usuario(nome_input, idade_input, altura_input))
```

### Quiz de Fixação
1. O Python impede a execução do código se você passar um tipo diferente do indicado no Type Hint?
   > **Resposta:** Não, o Type Hint é apenas informativo para o desenvolvedor e ferramentas de análise.
2. Como indicamos o tipo de retorno de uma função?
   > **Resposta:** Usando o símbolo `->` após os parênteses da função.
3. Para que serve o módulo `typing` (ex: `List`, `Dict`)?
   > **Resposta:** Para definir tipos mais complexos, como "uma lista que só contém inteiros" (`List[int]`).

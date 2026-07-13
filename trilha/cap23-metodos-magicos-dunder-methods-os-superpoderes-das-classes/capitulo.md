# Capítulo 23: Métodos Mágicos (Dunder Methods) – Os Superpoderes das Classes

### Teoria Sem Enrolação
Os métodos mágicos começam e terminam com dois underlines (Double Under, ou **Dunder**). Eles permitem que seus objetos se comportem como tipos nativos do Python.
- `__str__`: Define o que acontece quando você dá um `print(objeto)`.
- `__len__`: Define o que o `len(objeto)` deve contar.
- `__add__`: Define como dois objetos daquela classe devem ser somados usando o símbolo `+`.
- `__repr__`: Usado para representação de depuração (para desenvolvedores).

### A Grande Analogia
Imagine que você está criando um **Controle Remoto Universal**. 
No Python, existem botões padrão que todo mundo conhece: o botão "Ligar", o "Volume +" e o "Info".
O `__str__` é o botão "Info": você decide o que vai aparecer na tela quando ele for apertado. 
O `__add__` é o botão "+": você programa o controle para saber que, se alguém apertar "+", ele deve somar a potência dos dispositivos. 
Os métodos mágicos "ensinam" ao Python como usar os operadores padrão nos seus objetos customizados.

### Desafio de Aplicação CLI: "A Classe Livro Inteligente"
Crie uma classe `Livro` que tenha `titulo` e `paginas`.
1. Implemente o `__str__` para que, ao printar o livro, apareça: "Livro: [Título] - [Páginas] págs".
2. Implemente o `__len__` para que o Python saiba que o "tamanho" do livro é o seu número de páginas.
3. Implemente o `__add__` para que, se somarmos dois livros, o resultado seja a soma total de páginas de ambos.

### Gabarito do Desafio
```python
class Livro:
    def __init__(self, titulo, paginas):
        self.titulo = titulo
        self.paginas = paginas

    def __str__(self):
        return f"Livro: '{self.titulo}' - {self.paginas} págs"

    def __len__(self):
        return self.paginas

    def __add__(self, outro_livro):
        return self.paginas + outro_livro.paginas

# Testando os superpoderes
livro1 = Livro("Pense em Python", 300)
livro2 = Livro("Código Limpo", 450)

print(livro1) # Usa o __str__
print(f"Tamanho do livro 1: {len(livro1)}") # Usa o __len__
print(f"Total de páginas se ler os dois: {livro1 + livro2}") # Usa o __add__
```

### Quiz de Fixação
1. Por que os métodos mágicos são chamados de "dunder"?
   > **Resposta:** Por causa do "Double Underline" (sublinhado duplo) antes e depois do nome.
2. Qual método mágico é responsável pela comparação de igualdade (`==`) entre objetos?
   > **Resposta:** O método `__eq__`.
3. É obrigatório implementar métodos mágicos em toda classe?
   > **Resposta:** Não, apenas quando você quer que sua classe interaja com as funções e operadores nativos do Python.

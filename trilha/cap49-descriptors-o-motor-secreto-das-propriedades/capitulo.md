# Capítulo 49: Descriptors – O Motor Secreto das Propriedades

### Teoria Sem Enrolação
Você já se perguntou como o `@property` funciona? Ele é baseado em **Descriptors**. Um Descriptor é uma classe que define pelo menos um dos métodos mágicos: `__get__`, `__set__` ou `__delete__`. 
- Quando você atribui um valor a um atributo de um objeto, normalmente o Python apenas guarda na memória. 
- Com um Descriptor, você "sequestra" essa operação. Você pode validar dados, transformar strings ou registrar logs toda vez que alguém tentar ler ou escrever naquele atributo. É o nível mais alto de controle sobre o estado de um objeto em Python.

### A Grande Analogia
Imagine que um objeto é uma **Geladeira Inteligente**.
Os atributos normais são prateleiras abertas: qualquer um coloca qualquer coisa lá.
Um **Descriptor** é como uma **Gaveta de Biometria**. Você não consegue simplesmente "colocar" algo nela. Quando você tenta (`__set__`), a gaveta verifica se sua digital é válida e se o item que você está colocando é um alimento permitido. Quando você tenta "abrir" (`__get__`), ela pode registrar quem pegou o item. O Descriptor é o mecanismo de segurança que controla o acesso à gaveta, independentemente de quem seja o dono da geladeira.

### Desafio de Aplicação CLI: "O Validador de Preços Positivos"
Crie um Descriptor chamado `PrecoValido`. 
1. Ele não deve permitir que o preço de um produto seja definido como um valor negativo. 
2. Se o usuário tentar definir um valor negativo, o programa deve avisar que o valor foi ajustado para zero automaticamente.
3. Aplique esse descriptor em uma classe `Produto`.

### Gabarito do Desafio
```python
class PrecoValido:
    def __init__(self):
        self._nome_atributo = None

    def __set_name__(self, owner, name):
        self._nome_atributo = "_" + name

    def __get__(self, instance, owner):
        return getattr(instance, self._nome_atributo)

    def __set__(self, instance, valor):
        if valor < 0:
            print(f"Aviso: Preço negativo ({valor}) não permitido. Ajustando para 0.")
            setattr(instance, self._nome_atributo, 0)
        else:
            setattr(instance, self._nome_atributo, valor)

class Produto:
    preco = PrecoValido() # O descriptor controla o atributo 'preco'

    def __init__(self, nome, preco):
        self.nome = nome
        self.preco = preco

# Teste
p1 = Produto("Notebook", 3500)
p2 = Produto("Cabo USB", -15)

print(f"Produto: {p1.nome} | Preço: {p1.preco}")
print(f"Produto: {p2.nome} | Preço: {p2.preco}")
```

### Quiz de Fixação
1. Quais são os métodos que definem um descriptor?
   > **Resposta:** `__get__`, `__set__` e `__delete__`.
2. Qual a diferença entre um Descriptor e um `@property`?
   > **Resposta:** O `@property` é uma forma simplificada de criar um descriptor para um único atributo; o Descriptor é uma classe reutilizável que pode ser aplicada a vários atributos em classes diferentes.
3. Para que serve o método `__set_name__`?
   > **Resposta:** Ele serve para capturar automaticamente o nome do atributo ao qual o descriptor foi associado na classe.

# Capítulo 46: Metaclasses – A Fábrica de Fábricas

### Teoria Sem Enrolação
Em Python, tudo é um objeto. Incluindo as classes. Se uma classe é um objeto, quem criou essa classe? A resposta é a **Metaclasse**.
- Por padrão, a metaclasse de tudo em Python é a `type`.
- Ao criar sua própria metaclasse (herdando de `type`), você ganha o poder de interceptar a criação de uma classe. Você pode injetar métodos, mudar atributos ou validar regras no momento em que o programador define a classe, antes mesmo de qualquer objeto ser criado.
- É uma ferramenta de "magia negra" do Python, usada por frameworks como Django e SQLAlchemy.

### A Grande Analogia
Imagine que você trabalha na **Prefeitura das Indústrias**.
- Uma **Classe** comum é o **Projeto da Fábrica**.
- Um **Objeto** é a **Fábrica Construída**.
- A **Metaclasse** é a **Lei Municipal de Construção**. Ela não constrói fábricas, ela dita as regras para quem faz os projetos. Se alguém trouxer um projeto de fábrica sem saída de emergência (um método obrigatório), a Metaclasse (a Lei) impede o projeto de sequer ser aprovado. Ela controla como as classes devem ser formadas.

### Desafio de Aplicação CLI: "A Regra do Nome Minúsculo"
Crie uma metaclasse chamada `ForceLowercaseMeta`. Ela deve interceptar a criação de qualquer classe e transformar o nome de todos os seus atributos e métodos em letras minúsculas automaticamente.

### Gabarito do Desafio
```python
class ForceLowercaseMeta(type):
    # O método __new__ é chamado quando a classe está sendo criada
    def __new__(cls, name, bases, dct):
        lower_dct = {}
        for key, value in dct.items():
            # Se não for um método mágico, transforma em minúsculo
            if not key.startswith("__"):
                lower_dct[key.lower()] = value
            else:
                lower_dct[key] = value
        return super().__new__(cls, name, bases, lower_dct)

# Usando a metaclasse
class Teste(metaclass=ForceLowercaseMeta):
    VARIAVEL_GRITANDO = 10
    def METODO_BARULHENTO(self):
        print("Funcionou!")

objeto = Teste()
# O atributo agora só existe em minúsculo!
print(f"Atributo: {objeto.variavel_gritando}")
objeto.metodo_barulhento()
```

### Quiz de Fixação
1. Qual é a metaclasse padrão do Python para todas as classes?
   > **Resposta:** `type`.
2. Por que as metaclasses são chamadas de "Metaprogramação"?
   > **Resposta:** Porque é um código que escreve ou manipula outro código (no caso, a definição de classes).
3. Qual método da metaclasse é geralmente usado para modificar a estrutura de uma classe antes dela ser criada?
   > **Resposta:** O método `__new__`.

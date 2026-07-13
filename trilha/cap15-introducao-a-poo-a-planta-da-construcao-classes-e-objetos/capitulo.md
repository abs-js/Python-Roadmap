# Capítulo 15: Introdução à POO – A Planta da Construção (Classes e Objetos)

### Teoria Sem Enrolação
A Programação Orientada a Objetos (POO) é uma forma de organizar o código tentando imitar o mundo real.
- **Classe**: É o molde, a planta baixa, o conceito (ex: O conceito de "Cachorro").
- **Objeto**: É o item real criado a partir do molde (ex: O "Rex", que é um cachorro específico).
- **Atributos (`self.nome`)**: São as características (cor, raça, tamanho).
- **Métodos**: São as ações que o objeto faz (latir, correr, comer).
- **`__init__`**: É o método "Construtor". Ele roda no momento exato em que o objeto nasce.

### A Grande Analogia
Imagine uma **Fábrica de Carros**.
A **Classe** é o **Projeto de Engenharia** (o desenho no papel). O projeto diz que todo carro deve ter cor, motor e rodas.
O **Objeto** é o **Carro Físico** que sai da linha de montagem. Um objeto pode ser um "Fusca Azul" e outro pode ser uma "Ferrari Vermelha". Ambos vieram do mesmo projeto (Classe), mas têm características (Atributos) diferentes.

### Desafio de Aplicação CLI: "Simulador de Conta Bancária"
Crie uma classe chamada `ContaBancaria`.
1. Ela deve ter os atributos `titular` e `saldo`.
2. Ela deve ter um método chamado `depositar(valor)`.
3. Ela deve ter um método chamado `exibir_saldo()`.
Crie um objeto dessa classe, faça um depósito e exiba o saldo final.

### Gabarito do Desafio
```python
class ContaBancaria:
    def __init__(self, nome_titular):
        self.titular = nome_titular
        self.saldo = 0  # Toda conta começa com zero

    def depositar(self, valor):
        self.saldo += valor
        print(f"Depósito de R${valor} realizado com sucesso!")

    def exibir_saldo(self):
        print(f"Titular: {self.titular} | Saldo Atual: R${self.saldo}")

# Criando o objeto (instanciando a classe)
minha_conta = ContaBancaria("Professor Python")

# Usando os métodos
minha_conta.exibir_saldo()
minha_conta.depositar(500)
minha_conta.exibir_saldo()
```

### Quiz de Fixação
1. O que representa o parâmetro `self` dentro de uma classe?
   > **Resposta:** Representa o próprio objeto que está sendo manipulado no momento (é o "eu mesmo" do objeto).
2. Como chamamos a função que inicializa os atributos de uma classe?
   > **Resposta:** Construtor ou método `__init__`.
3. Qual a diferença entre Atributo e Método?
   > **Resposta:** Atributo é uma característica (variável do objeto); Método é uma ação (função do objeto).

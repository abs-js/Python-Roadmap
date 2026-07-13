# Capítulo 27: Classes Abstratas – O Contrato Obrigatório

### Teoria Sem Enrolação
Às vezes você quer criar uma classe pai, mas não quer que ninguém crie objetos diretamente dela. Você quer apenas que ela sirva de "modelo" para as filhas.
- Usamos o módulo **`abc`** (Abstract Base Classes).
- Um **`abstractmethod`** é um método que a classe pai define, mas **não implementa**. É uma promessa: "Toda classe filha que herdar de mim é OBRIGADA a criar sua própria versão deste método".

### A Grande Analogia
Imagine que o governo cria um decreto chamado **"Contrato do Meio de Transporte"**.
O decreto diz: "Todos os transportes devem ter um método chamado `locomover()`".
Você não pode "comprar um Meio de Transporte" genérico; isso não existe. Você compra um Carro ou uma Bicicleta. O decreto é a **Classe Abstrata**: ele só serve para garantir que, se você inventar um novo transporte, ele obrigatoriamente saiba se locomover, senão ele não poderá ser chamado de transporte.

### Desafio de Aplicação CLI: "Sistema de Processamento de Pagamentos"
1. Crie uma classe abstrata `Pagamento`.
2. Ela deve obrigar as filhas a terem um método `processar(valor)`.
3. Crie duas classes filhas: `Cartao` e `Boleto`.
4. Garanta que ninguém consiga criar um objeto apenas de `Pagamento`.

### Gabarito do Desafio
```python
from abc import ABC, abstractmethod

class Pagamento(ABC):
    @abstractmethod
    def processar(self, valor):
        pass

class Cartao(Pagamento):
    def processar(self, valor):
        print(f"Processando R$ {valor} no cartão... Autorizado!")

class Boleto(Pagamento):
    def processar(self, valor):
        print(f"Gerando boleto de R$ {valor}... Aguardando pagamento.")

# Isso aqui daria ERRO: p = Pagamento()

pg1 = Cartao()
pg1.processar(150.00)

pg2 = Boleto()
pg2.processar(45.00)
```

### Quiz de Fixação
1. O que acontece se uma classe filha não implementar um método marcado como `@abstractmethod`?
   > **Resposta:** O Python impedirá a criação (instanciação) de qualquer objeto dessa classe filha.
2. Qual classe deve ser herdada para tornar uma classe abstrata?
   > **Resposta:** A classe `ABC` do módulo `abc`.
3. Posso ter métodos normais (com implementação) dentro de uma classe abstrata?
   > **Resposta:** Sim, você pode misturar métodos comuns com métodos abstratos.

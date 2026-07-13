# Capítulo 26: Métodos Estáticos e de Classe – A Caixa de Ferramentas Independente

### Teoria Sem Enrolação
Em POO, nem todo método precisa acessar os dados do objeto (`self`).
- **`@staticmethod`**: É apenas uma função comum que vive dentro da classe por organização. Ela não acessa nada da classe nem do objeto.
- **`@classmethod`**: Recebe a própria classe como primeiro parâmetro (chamado de `cls`). É útil para criar "fábricas" de objetos (formas alternativas de criar uma instância).

### A Grande Analogia
Imagine uma **Fábrica de Pizzas**.
- Um método comum seria "Colocar Recheio", pois depende da pizza específica que está na esteira (`self`).
- Um **Método de Classe (`@classmethod`)** seria o "Tipo de Massa Padrão": ele define algo que vale para todas as pizzas daquela fábrica (`cls`).
- Um **Método Estático (`@staticmethod`)** seria uma "Calculadora de Troco" que fica no balcão: ela é útil para a pizzaria, mas não precisa saber de que sabor é a pizza ou quem é o dono da fábrica para funcionar. É só uma ferramenta útil guardada ali dentro.

### Desafio de Aplicação CLI: "O Conversor de Moedas da Empresa"
Crie uma classe `Banco`. 
1. Ela deve ter um `@staticmethod` chamado `converter_dolar` que recebe um valor em Reais e uma cotação e retorna o valor convertido.
2. Ela deve ter um `@classmethod` chamado `criar_conta_vip` que recebe apenas o nome do cliente e já cria um objeto da classe com saldo inicial de R$ 10.000,00.

### Gabarito do Desafio
```python
class Banco:
    def __init__(self, cliente, saldo):
        self.cliente = cliente
        self.saldo = saldo

    @staticmethod
    def converter_dolar(reais, cotacao):
        return reais / cotacao

    @classmethod
    def criar_conta_vip(cls, nome):
        return cls(nome, 10000.00)

# Usando o método estático (sem precisar criar um objeto antes)
valor_em_dolar = Banco.converter_dolar(500, 5.20)
print(f"R$ 500,00 equivalem a US$ {valor_em_dolar:.2f}")

# Usando o método de classe para fabricar um objeto VIP
conta_juliana = Banco.criar_conta_vip("Juliana")
print(f"Cliente: {conta_juliana.cliente} | Saldo: R$ {conta_juliana.saldo}")
```

### Quiz de Fixação
1. Qual decorador usamos para um método que não precisa acessar `self` nem `cls`?
   > **Resposta:** `@staticmethod`.
2. No `@classmethod`, qual o nome da convenção para o primeiro parâmetro recebido?
   > **Resposta:** `cls` (abreviação de class).
3. Para que servem geralmente os `classmethods`?
   > **Resposta:** Para criar métodos de fábrica que instanciam objetos de maneiras pré-configuradas.

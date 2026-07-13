# Capítulo 63: Property Decorators – Getters e Setters Elegantes

### Teoria Sem Enrolação
Em outras linguagens, usamos métodos como `get_preco()` e `set_preco()`. No Python, usamos o decorador **`@property`**. 
Ele permite que você transforme um método em um "atributo" aparente. 
- **`@property` (Getter):** Permite ler o valor (com lógica extra, se quiser).
- **`@atributo.setter` (Setter):** Permite gravar o valor com validação, mas o usuário usa como se fosse uma atribuição simples (`obj.preco = 10`), em vez de chamar uma função.
Isso mantém a interface da sua classe limpa enquanto protege os dados internos.

### A Grande Analogia
Imagine um **Termostato de Ar-Condicionado**. 
Na frente, existe apenas um seletor de temperatura (`atributo`). 
- Quando você gira o botão para 20 graus (faz um **Setter**), o termostato não apenas muda o número; ele verifica se os 20 graus são seguros para o motor e liga o compressor. 
- Quando você olha o visor para ver a temperatura (faz um **Getter**), ele pode te mostrar a temperatura em Celsius ou Fahrenheit, processando o dado antes de te exibir. 
O usuário só interage com o "botão", mas por trás dele existe toda uma lógica de controle e validação.

### Desafio de Aplicação CLI: "O Cofre com Validação"
Crie uma classe `ContaCorrente`.
1. Ela deve ter um atributo privado `_saldo`.
2. Use `@property` para permitir ler o saldo.
3. Use um setter para o saldo que **não permita** que o saldo seja definido como negativo. Se tentarem colocar um valor negativo, exiba um erro e não mude o valor.

### Gabarito do Desafio
```python
class ContaCorrente:
    def __init__(self, saldo_inicial):
        self._saldo = saldo_inicial # Atributo 'protegido'

    @property
    def saldo(self):
        print("Consultando saldo...")
        return f"R$ {self._saldo:.2f}"

    @saldo.setter
    def saldo(self, novo_valor):
        if novo_valor < 0:
            print("ERRO: O saldo não pode ser negativo!")
        else:
            print(f"Atualizando saldo para {novo_valor}...")
            self._saldo = novo_valor

# Teste
minha_conta = ContaCorrente(1000)

print(minha_conta.saldo)      # Chama o Getter
minha_conta.saldo = 1500      # Chama o Setter (Sucesso)
minha_conta.saldo = -500      # Chama o Setter (Erro de validação)
print(minha_conta.saldo)
```

### Quiz de Fixação
1. Qual a vantagem de usar `@property` em vez de deixar o atributo público?
   > **Resposta:** Permite adicionar validação e lógica de processamento sem mudar a forma como o usuário acessa o dado.
2. Como chamamos o método que define a regra para "escrever" em uma propriedade?
   > **Resposta:** Setter.
3. É obrigatório criar um Setter para toda `@property`?
   > **Resposta:** Não, se você criar apenas o `@property` sem o setter, o seu atributo se tornará "somente leitura" (Read-only).

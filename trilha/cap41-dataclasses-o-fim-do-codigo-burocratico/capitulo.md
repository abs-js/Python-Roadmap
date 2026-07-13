# Capítulo 41: Dataclasses — O Fim do Código Burocrático

### Teoria Sem Enrolação
Criar classes apenas para guardar dados costuma ser chato: você precisa escrever o `__init__`, o `__repr__` para o print ficar bonito, o `__eq__` para comparar objetos, etc.
As **Dataclasses** (módulo `dataclasses`) automatizam tudo isso. Você define apenas os campos e os tipos, e o Python escreve os métodos mágicos para você nos bastidores. O código fica muito mais limpo e focado no que importa: os dados.

### A Grande Analogia
Imagine que você trabalha em um **Cartório**. 
Antigamente (classe normal), para cada novo registro, você tinha que redigir o contrato inteiro à mão, repetindo todas as cláusulas padrão.
Com as **Dataclasses**, você recebe um **Formulário Pré-Impresso**. Você só precisa preencher as lacunas (os dados). O "texto jurídico" (métodos como init e repr) já vem impresso de fábrica pela própria gráfica do Python.

### Desafio de Aplicação CLI: "O Inventário de Espaçonaves"
1. Importe `dataclass` de `dataclasses`.
2. Crie uma dataclass chamada `Nave` com os campos: `nome` (str), `modelo` (str) e `tripulantes` (int).
3. Crie dois objetos de nave com os mesmos dados e use o operador `==` para ver se o Python entende que elas são iguais (coisa que ele não faria em classes normais sem código extra).

### Gabarito do Desafio
```python
from dataclasses import dataclass

@dataclass
class Nave:
    nome: str
    modelo: str
    tripulantes: int

# Criando as naves
nave1 = Nave("Millennium Falcon", "YT-1300", 4)
nave2 = Nave("Millennium Falcon", "YT-1300", 4)

print(nave1) # O print já sai formatado graças ao __repr__ automático
print(f"As naves são iguais? {nave1 == nave2}") # O __eq__ automático funciona!
```

### Quiz de Fixação
1. Qual decorador é necessário para transformar uma classe normal em uma dataclass?
   > **Resposta:** O decorador `@dataclass`.
2. As dataclasses permitem definir valores padrão para os campos?
   > **Resposta:** Sim, basta fazer `campo: tipo = valor_padrao` dentro da classe.
3. Dataclasses substituem completamente as classes normais?
   > **Resposta:** Não. Elas são ideais para classes que focam em armazenar estados (dados). Para classes com lógicas de comportamento complexas, as classes tradicionais ainda são muito usadas.

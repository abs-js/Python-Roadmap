# Capítulo 58: PyTest – O Canivete Suíço dos Testes Modernos

### Teoria Sem Enrolação
Vimos o `unittest`, que é nativo do Python, mas no "mundo real", o **PyTest** é o rei. Ele é mais simples, mais potente e exige muito menos código.
- **Fixtures:** Funções que preparam o terreno (ex: criam um banco de dados temporário) antes do teste rodar e o limpam depois.
- **Injeção de Dependência:** O PyTest passa essas fixtures automaticamente para seus testes apenas pelo nome do argumento.
- **Asserções simples:** Você usa o `assert` puro do Python em vez de `self.assertEqual()`. Se o teste falhar, o PyTest te mostra exatamente o que estava dentro da variável de um jeito muito visual.

### A Grande Analogia
Imagine que você é um **Mecânico de Fórmula 1**.
O `unittest` seria você ter que assinar 10 formulários e carregar sua própria caixa de ferramentas pesada para cada carro que chega.
O **PyTest** é como ter uma **Oficina Inteligente**. Se você escrever um teste que precisa de um "elevador" (uma fixture), no momento em que você começa o teste, o elevador já aparece embaixo do carro magicamente. Você só se preocupa em consertar o motor, sem se preocupar em como as ferramentas chegaram ali.

### Desafio de Aplicação CLI: "O Testador de Descontos"
1. Crie uma função `calcular_desconto(valor, percentual)`.
2. Use o PyTest para criar uma **fixture** que sempre retorne um valor base de 100.
3. Escreva um teste que verifique se um desconto de 10% sobre o valor da fixture resulta em 90.
4. Escreva outro que verifique se um desconto de 0% mantém o valor original.

### Gabarito do Desafio
```python
import pytest

# A função a ser testada
def calcular_desconto(valor, percentual):
    return valor - (valor * (percentual / 100))

# Criando a Fixture (o cenário preparado)
@pytest.fixture
def valor_base():
    return 100

# O teste recebe a fixture 'valor_base' como argumento
def test_desconto_dez_por_cento(valor_base):
    assert calcular_desconto(valor_base, 10) == 90

def test_sem_desconto(valor_base):
    assert calcular_desconto(valor_base, 0) == 100

# Para rodar: pytest nome_do_arquivo.py no terminal
```

### Quiz de Fixação
1. Qual a principal vantagem visual do PyTest em relação ao Unittest quando um teste falha?
   > **Resposta:** Ele faz a introspecção do erro, mostrando o valor real de cada variável envolvida na falha de forma detalhada.
2. Como se chama a ferramenta do PyTest usada para preparar dados para os testes?
   > **Resposta:** Fixture.
3. O PyTest consegue rodar testes escritos anteriormente usando a biblioteca `unittest`?
   > **Resposta:** Sim, ele possui total compatibilidade com testes legados do unittest.

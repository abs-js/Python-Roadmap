# Capítulo 31: Testes Unitários – O Inspetor de Qualidade

### Teoria Sem Enrolação
Programar sem testar é como construir uma ponte e esperar que o primeiro caminhão passe para saber se ela aguenta. **Testes Unitários** são pequenos scripts que verificam se uma parte específica do seu código (uma função ou classe) faz exatamente o que deveria fazer.
- No Python, usamos o módulo nativo `unittest` ou a biblioteca popular `pytest`.
- O conceito principal é o **`assert`** (afirmação). Você diz: "Eu afirmo que o resultado da função X com os dados Y deve ser Z". Se não for, o teste falha e você descobre o erro antes do cliente.

### A Grande Analogia
Imagine que você é um **Fabricante de Paraquedas**. 
Você não vai esperar alguém pular do avião para saber se o paraquedas abre. Em vez disso, você cria uma **Bancada de Testes** na fábrica. Você coloca o paraquedas em uma máquina que puxa a corda com uma força específica e verifica se ele abre em menos de 2 segundos. 
O seu código é o paraquedas. O teste unitário é a máquina da bancada que garante que cada peça está funcionando perfeitamente antes de sair da fábrica.

### Desafio de Aplicação CLI: "O Laboratório de Testes de Calculadora"
Crie um arquivo chamado `operacoes.py` com uma função `somar(a, b)`. Em seguida, crie um script de teste que use o módulo `unittest` para verificar três cenários:
1. Se 2 + 3 é igual a 5.
2. Se -1 + 1 é igual a 0.
3. Se 0 + 0 é igual a 0.

### Gabarito do Desafio
```python
import unittest

# A função que queremos testar (poderia estar em outro arquivo)
def somar(a, b):
    return a + b

# A classe de testes
class TestSoma(unittest.TestCase):
    def test_soma_positivos(self):
        self.assertEqual(somar(2, 3), 5)

    def test_soma_negativos(self):
        self.assertEqual(somar(-1, 1), 0)

    def test_soma_zeros(self):
        self.assertEqual(somar(0, 0), 0)

if __name__ == "__main__":
    unittest.main()
```

### Quiz de Fixação
1. Qual o objetivo principal de um teste unitário?  
   > **Resposta:** Verificar se uma pequena unidade de código (função ou método) funciona conforme o esperado de forma isolada.
2. O que acontece quando um comando `assert` recebe uma condição falsa?  
   > **Resposta:** O Python levanta um erro do tipo `AssertionError` e o teste falha.
3. Para que serve o método `assertEqual(a, b)` no unittest?  
   > **Resposta:** Para verificar se o valor `a` é exatamente igual ao valor `b`.

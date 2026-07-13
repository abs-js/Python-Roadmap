# Capítulo 64: Mocking – O Dublê de Testes

### Teoria Sem Enrolação
Quando você testa uma função que envia um e-mail real ou deleta um arquivo no servidor, você tem um problema: o teste pode ser lento, caro ou perigoso. O **Mocking** (usando `unittest.mock`) resolve isso criando objetos "falsos" que fingem ser objetos reais. 
- Você pode configurar o que o Mock deve retornar quando for chamado.
- Você pode verificar se o seu código realmente tentou chamar aquela função e com quais argumentos.
- É essencial para isolar o seu código de dependências externas (APIs, Bancos de Dados, Sensores).

### A Grande Analogia
Imagine que você está filmando uma **Cena de Ação de um Filme**.
Você não vai explodir um prédio de verdade toda vez que o diretor gritar "Ação" apenas para ver se o ator corre rápido o suficiente. Para os ensaios, você usa um **Cenário de Papelão** e um **Dublê**. 
O Dublê (Mock) se parece com o ator, mas ele só serve para simular a presença dele. No final, você não quer saber se o prédio explodiu, mas sim se o ator executou os movimentos certos na hora em que o "falso prédio" (o mock) deu o sinal.

### Desafio de Aplicação CLI: "O Simulador de Pagamento com API"
Crie uma função `processar_venda(valor, api_pagamento)`. 
1. Ela deve chamar `api_pagamento.autorizar(valor)`.
2. Se a API retornar `True`, a função retorna "Venda Concluída".
3. Use o `MagicMock` para simular a API e garantir que seu código trata corretamente tanto o retorno `True` quanto o `False`, sem precisar de uma conexão real com a internet.

### Gabarito do Desafio
```python
from unittest.mock import MagicMock

def processar_venda(valor, api_pagamento):
    # Chamamos o método da API (que será um dublê)
    if api_pagamento.autorizar(valor):
        return "Venda Concluída"
    else:
        return "Venda Negada"

# 1. Criamos o dublê
mock_api = MagicMock()

# 2. Configuramos o comportamento do dublê para retornar True
mock_api.autorizar.return_value = True
print(f"Teste 1: {processar_venda(100, mock_api)}")

# 3. Verificamos se o código realmente chamou a API corretamente
mock_api.autorizar.assert_called_with(100)

# 4. Configuramos para falhar
mock_api.autorizar.return_value = False
print(f"Teste 2: {processar_venda(100, mock_api)}")
```

### Quiz de Fixação
1. Qual a diferença entre um objeto real e um Mock em um teste?  
   > **Resposta:** O objeto real executa a lógica verdadeira; o Mock apenas simula a interface e retorna valores pré-configurados.
2. Como verificamos se um mock foi chamado pelo menos uma vez?  
   > **Resposta:** Usando o método `assert_called()`.
3. O que acontece se chamarmos um método em um `MagicMock` que não definimos anteriormente?  
   > **Resposta:** Ele não dará erro; o `MagicMock` cria o método automaticamente na hora e retorna outro objeto mock.

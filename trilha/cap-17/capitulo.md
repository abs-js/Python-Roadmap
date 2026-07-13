# Capítulo 17: Decoradores (Decorators) – A Função que Envolve

### Teoria Sem Enrolação
Decoradores são "embrulhos" para suas funções. Eles permitem que você execute um código **antes** e **depois** de uma função principal, sem precisar alterar o código dela.
- Sua sintaxe utiliza o símbolo `@` acima da definição da função.
- É muito usado para: medir tempo de execução, verificar se o usuário está logado ou registrar logs.

### A Grande Analogia
Imagine que você tem uma função chamada `comer_hamburguer()`. 
O **Decorador** é como os **Acompanhamentos**. 
Sem mudar o hambúrguer, o decorador adiciona uma "camada extra": ele pode lavar as mãos (ação antes) e limpar a mesa (ação depois). A função principal (comer) continua a mesma, mas o decorador garantiu que o ambiente estivesse preparado.

### Desafio de Aplicação CLI: "O Decorador de Log"
Crie um decorador chamado `aviso_execucao`. Ele deve imprimir "Iniciando tarefa..." antes de qualquer função que ele decorar e "Tarefa finalizada!" depois. Aplique-o em uma função simples que simula o processamento de um pagamento.

### Gabarito do Desafio
```python
def aviso_execucao(funcao_original):
    def wrapper():
        print(">>> [LOG]: Iniciando tarefa...")
        funcao_original()
        print(">>> [LOG]: Tarefa finalizada com sucesso!")
    return wrapper

@aviso_execucao
def processar_pagamento():
    print("Processando pagamento de R$ 200,00...")

# Executando
processar_pagamento()
```

### Quiz de Fixação
1. Qual símbolo identifica o uso de um decorador em Python?
   > **Resposta:** O símbolo `@`.
2. O que é a função `wrapper` dentro de um decorador?
   > **Resposta:** É a função interna que "embrulha" a original, permitindo executar códigos antes e depois.
3. Decoradores alteram o código-fonte da função original?
   > **Resposta:** Não, eles apenas adicionam funcionalidades ao redor dela.

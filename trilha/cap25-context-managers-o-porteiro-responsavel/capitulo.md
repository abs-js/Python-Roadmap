# Capítulo 25: Context Managers – O Porteiro Responsável

### Teoria Sem Enrolação
Você já usou o `with open(...)`, mas sabia que pode criar seu próprio `with`? Isso se chama **Context Manager**. 
Ele serve para automatizar duas ações: configurar algo ao entrar em um bloco de código (`__enter__`) e limpar a bagunça ao sair (`__exit__`). É a melhor forma de garantir que recursos preciosos (como conexões de banco de dados, arquivos ou acesso à internet) não fiquem "abertos" por erro, travando o sistema.

### A Grande Analogia
Imagine que você vai alugar uma **Sala de Festas**. 
O **Context Manager** é o **Contrato de Aluguel**:
- O `__enter__` é o momento que você pega as chaves e confere se as luzes estão funcionando. 
- O bloco de código é a **Festa** propriamente dita. 
- O `__exit__` é o final da noite: não importa se a festa foi ótima ou se alguém quebrou um copo (ocorreu um erro), o porteiro garante que as luzes sejam apagadas, o lixo recolhido e a porta trancada antes de você ir embora.

### Desafio de Aplicação CLI: "O Cronômetro de Operações"
Crie um Context Manager chamado `Temporizador`. Quando usado com o comando `with`, ele deve imprimir "Iniciando cronômetro..." e, ao finalizar o bloco de código, deve calcular e exibir quantos segundos se passaram.

### Gabarito do Desafio
```python
import time

class Temporizador:
    def __enter__(self):
        self.inicio = time.time()
        print(">>> [LOG]: Iniciando cronômetro...")
        return self

    def __exit__(self, tipo_erro, valor_erro, traceback):
        self.fim = time.time()
        duracao = self.fim - self.inicio
        print(f">>> [LOG]: Tempo total decorrido: {duracao:.4f} segundos.")

# Usando o nosso próprio Context Manager
with Temporizador():
    print("Executando uma tarefa demorada...")
    time.sleep(2) # Pausa o código por 2 segundos
    print("Tarefa concluída!")
```

### Quiz de Fixação
1. Quais são os dois métodos mágicos necessários para criar um Context Manager em uma classe?
   > **Resposta:** `__enter__` e `__exit__`.
2. O que acontece se ocorrer um erro dentro de um bloco `with`?
   > **Resposta:** O método `__exit__` ainda será executado, garantindo o fechamento dos recursos.
3. Além de classes, existe outra forma de criar Context Managers em Python?
   > **Resposta:** Sim, usando o decorador `@contextmanager` do módulo `contextlib`.

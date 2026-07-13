# Capítulo 68: Decoradores com Argumentos – O Próximo Nível da Customização

### Teoria Sem Enrolação
Vimos que um decorador "embrulha" uma função. Mas e se quisermos passar configurações para esse embrulho? Por exemplo, um decorador que repete uma função 3 vezes, ou 10 vezes?
Para isso, precisamos de um **terceiro nível de funções**:
1. Uma função externa que recebe os **argumentos do decorador**.
2. Uma função intermediária que recebe a **função original**.
3. Uma função interna (`wrapper`) que executa a **lógica final**.
Parece confuso, mas é a chave para criar ferramentas de código altamente flexíveis.

### A Grande Analogia
Imagine que você tem uma **Máquina de Pintar Carros**.
Um decorador simples é uma máquina que pinta de azul. Todo carro que passa por ela sai azul.
Um **Decorador com Argumentos** é uma máquina que tem um **Painel de Controle**. Antes do carro entrar, você ajusta a cor no painel: "Pinte de Vermelho, com Brilho, 2 camadas". A máquina (decorador) se ajusta conforme as suas instruções antes de começar o trabalho no carro (a função).

### Desafio de Aplicação CLI: "O Repetidor de Tarefas"
Crie um decorador chamado `repetir(vezes=3)`.
1. Ele deve receber um número como argumento.
2. Ele deve executar a função decorada a quantidade de vezes especificada.
3. Aplique esse decorador em uma função `saudar()` que imprime "Olá mundo!".

### Gabarito do Desafio
```python
def repetir(vezes):
    def decorador_real(funcao):
        def wrapper(*args, **kwargs):
            for _ in range(vezes):
                resultado = funcao(*args, **kwargs)
            return resultado
        return wrapper
    return decorador_real

# Usando o decorador configurado para rodar 5 vezes
@repetir(vezes=5)
def saudar():
    print("Olá mundo!")

saudar()
```

### Quiz de Fixação
1. Quantos níveis de funções aninhadas (uma dentro da outra) são necessários para um decorador com argumentos?
   > **Resposta:** Três níveis.
2. Onde os argumentos passados entre parênteses no `@decorador(arg)` são capturados?
   > **Resposta:** Na função mais externa.
3. Como garantimos que a função decorada continue funcionando mesmo se receber parâmetros?
   > **Resposta:** Usando `*args` e `**kwargs` na função `wrapper`.

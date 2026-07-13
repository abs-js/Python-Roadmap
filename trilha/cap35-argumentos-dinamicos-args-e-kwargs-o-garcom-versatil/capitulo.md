# Capítulo 35: Argumentos Dinâmicos (*args e **kwargs) — O Garçom Versátil

### Teoria Sem Enrolação
Às vezes você não sabe quantos argumentos o usuário vai passar para sua função. 
- **`*args` (Arguments):** Permite receber um número ilimitado de argumentos posicionais. O Python os empacota em uma **Tupla**.
- **`**kwargs` (Keyword Arguments):** Permite receber um número ilimitado de argumentos nomeados (ex: `cor="azul"`). O Python os empacota em um **Dicionário**.
Isso dá uma flexibilidade imensa para criar funções genéricas ou decoradores.

### A Grande Analogia
Imagine que você é um **Garçom em um Restaurante de Luxo**.
- O `*args` é como o cliente dizer: "Traga-me **todas as bebidas** que você tiver". Ele não disse quantas, nem quais. Você pega todas, coloca em uma bandeja (tupla) e entrega na mesa.
- O `**kwargs` é como o cliente dizer: "Eu quero o prato de acordo com estas **especificações**: ponto=mal_passado, acompanhamento=fritas". Ele deu nomes aos pedidos. Você anota tudo em uma comanda (dicionário) para o chef ler.

### Desafio de Aplicação CLI: "O Super Somador e Perfil de Usuário"
1. Crie uma função `multi_soma(*args)` que some todos os números passados, não importa se forem 2 ou 200.
2. Crie uma função `exibir_perfil(nome, **kwargs)` que imprima o nome e depois percorra o dicionário de argumentos extras imprimindo "Chave: Valor".

### Gabarito do Desafio
```python
def multi_soma(*args):
    total = sum(args)
    print(f"Somando {len(args)} números. Total: {total}")

def exibir_perfil(nome, **kwargs):
    print(f"\n--- Perfil de {nome} ---")
    for chave, valor in kwargs.items():
        print(f"{chave.capitalize()}: {valor}")

# Testando
multi_soma(10, 20, 30, 40)
exibir_perfil("Carlos", idade=30, cidade="São Paulo", profissao="Dev")
```

### Quiz de Fixação
1. Qual o tipo de dado de `args` dentro da função?
   > **Resposta:** Tupla.
2. Qual o tipo de dado de `kwargs` dentro da função?
   > **Resposta:** Dicionário.
3. Posso usar nomes diferentes de `args` e `kwargs`?
   > **Resposta:** Sim, o que importa é o uso de um asterisco `*` ou dois `**`, mas `args` e `kwargs` são os padrões da comunidade.

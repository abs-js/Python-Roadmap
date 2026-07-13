# Capítulo 19: Iterators e Generators – A Economia de Memória

### Teoria Sem Enrolação
Imagine que você precisa processar uma lista de 1 bilhão de números. Se você criar uma lista tradicional, o seu computador vai travar por falta de memória RAM. 
- **Iterators:** São objetos que permitem percorrer uma coleção um item por vez (usando a função `next()`).
- **Generators:** São funções especiais que usam a palavra-chave **`yield`** em vez de `return`. Quando uma função encontra um `yield`, ela "pausa" a execução, devolve um valor e fica esperando ser chamada novamente para continuar de onde parou. Eles não guardam todos os dados na memória; eles geram o próximo item "sob demanda".

### A Grande Analogia
Imagine a diferença entre uma **Jarra de Suco** e um **Filtro de Água de Parede**.
Uma lista é a **Jarra**: você tem que encher a jarra inteira (gastar memória) antes de começar a beber. Se a jarra for gigante, você não consegue nem levantá-la.
Um Generator é o **Filtro**: a água não está lá parada ocupando espaço. Assim que você abre a torneira (chama o `next`), o filtro processa a água e te entrega um copo. Ele só gasta o espaço de um copo por vez, não importa se você vai beber 1 litro ou 1000 litros.

### Desafio de Aplicação CLI: "O Contador Infinito e Econômico"
Crie uma função generator chamada `gerador_pares(limite)`. Ela deve gerar apenas números pares até o limite definido, sem criar uma lista. No programa principal, use um loop `for` para imprimir esses números.

### Gabarito do Desafio
```python
def gerador_pares(limite):
    numero = 0
    while numero <= limite:
        yield numero  # Aqui a função pausa e entrega o valor
        numero += 2

# Usando o generator
# Note que não estamos consumindo RAM para guardar todos os números
print("Listando pares de forma econômica:")
for par in gerador_pares(10):
    print(par)

# Testando o consumo sob demanda com next
meu_gen = gerador_pares(4)
print(next(meu_gen)) # Saída: 0
print(next(meu_gen)) # Saída: 2
```

### Quiz de Fixação
1. Qual a palavra-chave que transforma uma função comum em um Generator?
   > **Resposta:** `yield`.
2. O que acontece com os dados de um Generator depois que você termina de percorrê-lo?
   > **Resposta:** Eles são "consumidos" e descartados da memória; você precisaria reiniciar o generator para vê-los de novo.
3. Qual a principal vantagem de usar Generators em vez de Listas para grandes volumes de dados?
   > **Resposta:** Economia drástica de memória RAM.

# Capítulo 56: __slots__ – A Prateleira Sob Medida (Otimização)

### Teoria Sem Enrolação
Por padrão, o Python guarda os atributos de cada objeto em um dicionário escondido chamado `__dict__`. Dicionários são flexíveis (você pode adicionar atributos novos a qualquer momento), mas gastam muita memória RAM.
Se você vai criar **milhões** de objetos de uma classe que sempre tem os mesmos atributos (ex: um sistema de partículas ou coordenadas de mapa), você pode usar o atributo **`__slots__`**.
- Ele diz ao Python: "Não crie um dicionário para cada objeto. Guarde apenas estes atributos específicos".
- Isso economiza muita memória e acelera o acesso aos atributos.
- **Efeito colateral:** Você não conseguirá adicionar atributos dinâmicos que não estejam listados no `__slots__`.

### A Grande Analogia
Imagine que você está organizando uma **Coleção de Relógios**.
- O método padrão (`__dict__`) é como dar a cada relógio uma **Caixa de Papelão Gigante**. Você pode colocar o relógio lá e, se quiser, jogar uma pulseira extra, uma pilha ou um recibo. É flexível, mas sua estante fica cheia rápido porque as caixas ocupam muito espaço vazio.
- O **`__slots__`** é como criar um **Expositor Sob Medida** com furos exatos para o relógio e nada mais. Você não consegue colocar nada extra, mas consegue colocar 10 vezes mais relógios na mesma estante, tudo organizado e compacto.

### Desafio de Aplicação CLI: "O Comparador de Peso de Objetos"
Use o módulo `sys` para comparar o tamanho na memória de um objeto comum e um objeto com `__slots__`.
1. Crie uma classe `PontoComum` com `x` e `y`.
2. Crie uma classe `PontoOtimizado` com `__slots__ = ('x', 'y')`.
3. Tente adicionar um atributo `z` ao `PontoOtimizado` e veja o erro acontecer.

### Gabarito do Desafio
```python
import sys

class PontoComum:
    def __init__(self, x, y):
        self.x = x
        self.y = y

class PontoOtimizado:
    __slots__ = ('x', 'y')
    def __init__(self, x, y):
        self.x = x
        self.y = y

p1 = PontoComum(10, 20)
p2 = PontoOtimizado(10, 20)

# Comparando (Note que o sys.getsizeof nem sempre pega o dict interno, 
# mas em larga escala a diferença de RAM é massiva)
print(f"Objeto comum tem __dict__? {hasattr(p1, '__dict__')}")
print(f"Objeto otimizado tem __dict__? {hasattr(p2, '__dict__')}")

try:
    p2.z = 30
except AttributeError:
    print("Sucesso: Não foi possível adicionar 'z' ao objeto com slots!")
```

### Quiz de Fixação
1. Qual a principal vantagem de usar `__slots__`?
   > **Resposta:** Economia significativa de memória RAM em aplicações que instanciam muitos objetos.
2. Posso adicionar novos atributos a um objeto de uma classe que define `__slots__` em tempo de execução?
   > **Resposta:** Não, apenas os atributos listados no `__slots__` podem existir.
3. O que acontece com o atributo mágico `__dict__` quando usamos `__slots__`?
   > **Resposta:** Ele deixa de existir para as instâncias daquela classe, economizando espaço.

# Capítulo 55: MRO (Method Resolution Order) – A Árvore Genealógica

### Teoria Sem Enrolação
Python permite a **Herança Múltipla**, ou seja, uma classe pode ter vários pais (Ex: `class Filho(Pai, Mae):`). O problema surge quando tanto o Pai quanto a Mae possuem um método com o mesmo nome (ex: `falar()`). Qual deles o Python deve executar?
Para resolver isso, o Python utiliza o **MRO (Method Resolution Order)**, baseado em um algoritmo chamado **C3 Linearization**. 
- Ele cria uma lista prioritária de classes para buscar um método.
- Você pode visualizar essa ordem chamando o método `.mro()` ou o atributo `__mro__` em qualquer classe.
- A regra básica é: da esquerda para a direita e de baixo para cima (da classe mais específica para a mais genérica).

### A Grande Analogia
Imagine uma **Disputa de Herança Familiar**. 
Um jovem (a Classe Filho) quer saber como preparar uma receita de família chamada `fazer_bolo()`. 
1. Primeiro, ele olha no seu próprio caderno de receitas. 
2. Se não achar, ele olha no caderno do **Pai** (o primeiro na lista de herança). 
3. Se o pai não tiver, ele olha no caderno da **Mãe**.
4. Se ninguém tiver, ele vai até o **Avô** comum a ambos.
O MRO é o **Mapa Genealógico** que o advogado da família (o Python) usa para decidir qual testamento tem prioridade, garantindo que não haja confusão se dois parentes deixarem instruções conflitantes.

### Desafio de Aplicação CLI: "O Conflito de Poder dos Super-Heróis"
1. Crie uma classe `Voador` com o método `mover()` que imprime "Estou voando!".
2. Crie uma classe `Corredor` com o método `mover()` que imprime "Estou correndo!".
3. Crie uma classe `SuperHeroi` que herda de `Voador` e `Corredor` (nessa ordem).
4. Instancie o herói, chame o método `mover()` e depois imprima a ordem do MRO da classe para entender por que ele escolheu aquela forma de se mover.

### Gabarito do Desafio
```python
class Voador:
    def mover(self):
        print("Estou voando!")

class Corredor:
    def mover(self):
        print("Estou correndo!")

class SuperHeroi(Voador, Corredor):
    pass

# Criando o herói
heroi = SuperHeroi()

# Qual mover será chamado? O primeiro na lista de herança (Voador)
heroi.mover()

# Visualizando a ordem de resolução
print("\nOrdem de busca (MRO):")
for classe in SuperHeroi.mro():
    print(classe)
```

### Quiz de Fixação
1. Qual método ou atributo usamos para ver a ordem de prioridade de herança de uma classe?
   > **Resposta:** O método `mro()` ou o atributo `__mro__`.
2. Em `class C(A, B):`, se as duas classes pais tiverem o mesmo método, qual terá prioridade?
   > **Resposta:** A classe `A`, pois aparece primeiro (mais à esquerda) na definição.
3. O MRO garante que a classe base `object` seja sempre a última a ser consultada?
   > **Resposta:** Sim, em Python 3 todas as classes herdam de `object`, e ele é sempre o destino final da busca.

# Capítulo 16: POO Avançado – Herança e Polimorfismo

### Teoria Sem Enrolação
Na Programação Orientada a Objetos, você não precisa repetir código para objetos parecidos.
- **Herança**: Uma classe (Filha) pode herdar todos os atributos e métodos de outra classe (Pai). Usamos isso para criar especializações. Ex: Todo `Carro` é um `Veiculo`.
- **Polimorfismo**: É a capacidade de uma classe filha modificar um comportamento que herdou do pai. Embora o método tenha o mesmo nome, ele age de forma diferente. 
- **`super()`**: Um comando usado dentro da classe filha para chamar o construtor ou métodos da classe pai.

### A Grande Analogia
Pense na **Evolução Biológica**.
A classe pai é o **Mamífero**. Todo mamífero respira e tem sangue quente.
A classe filha **Cachorro** herda essas características de "Mamífero", mas adiciona a "especialização" de latir.
Já a classe filha **Gato** também herda de "Mamífero", mas implementa o método de "fazer som" de forma diferente (mia em vez de latir). Isso é o polimorfismo: a ação "emitir som" existe para ambos, mas cada um executa à sua maneira.

### Desafio de Aplicação CLI: "O Zoológico Polimórfico"
1. Crie uma classe pai chamada `Animal` com um método `falar()`.
2. Crie duas classes filhas: `Cachorro` e `Gato`.
3. Sobrescreva o método `falar()` em ambas para que o cachorro diga "Au Au" e o gato "Miau".
4. Crie uma lista com um objeto de cada animal e use um `for` para fazer todos "falarem".

### Gabarito do Desafio
```python
class Animal:
    def __init__(self, nome):
        self.nome = nome

    def falar(self):
        pass # Método genérico que será sobrescrito

class Cachorro(Animal):
    def falar(self):
        return f"{self.nome} diz: Au Au!"

class Gato(Animal):
    def falar(self):
        return f"{self.nome} diz: Miau!"

# Testando o Polimorfismo
animais = [Cachorro("Rex"), Gato("Frajola"), Cachorro("Thor")]

for animal in animais:
    print(animal.falar())
```

### Quiz de Fixação
1. Como chamamos quando uma classe herda características de outra?
   > **Resposta:** Herança.
2. Para que serve a função `super()`?
   > **Resposta:** Para acessar métodos ou o construtor da classe pai (superclasse) de dentro da classe filha.
3. Se a classe `Carro` herda de `Veiculo`, quem é a subclasse?
   > **Resposta:** `Carro`.

# Capítulo 57: Closures (Fechamentos) – A Memória Seletiva das Funções

### Teoria Sem Enrolação
Uma **Closure** ocorre quando uma função interna "lembra" e mantém acesso às variáveis da função externa que a criou, mesmo depois que a função externa já terminou de executar.
Para ser uma closure, precisamos de três coisas:
1. Uma função dentro de outra função.
2. A função interna usa uma variável da função externa.
3. A função externa retorna a função interna.
Isso é útil para criar funções com "memória" ou "configurações" sem usar classes.

### A Grande Analogia
Imagine que você vai a uma **Vidente**. 
Ela te entrega uma **Pocinha Mágica** (a função interna) que contém um segredo que ela sussurrou antes de sumir (a variável externa). A vidente foi embora (a função externa terminou), mas sempre que você olha para a poção, o segredo dela continua lá, preservado dentro do frasco. A poção "fechou" (closure) o ambiente ao redor do segredo.

### Desafio de Aplicação CLI: "O Gerador de Multiplicadores"
Crie uma função chamada `criar_multiplicador(n)`. 
1. Ela deve retornar uma função interna que recebe um número `x` e o multiplica por `n`.
2. Use-a para criar uma função `dobrar` e uma função `triplicar`.
3. Teste as duas e veja como cada uma "lembrou" do seu valor de `n` original.

### Gabarito do Desafio
```python
def criar_multiplicador(n):
    # Esta é a função interna que se tornará a closure
    def multiplicar(x):
        return x * n
    return multiplicar

# Criando instâncias de funções com memórias diferentes
dobrar = criar_multiplicador(2)
triplicar = criar_multiplicador(3)

print(f"Dobro de 10: {dobrar(10)}")      # Saída: 20
print(f"Triplo de 10: {triplicar(10)}")  # Saída: 30

# O valor '2' e '3' estão guardados no 'scopo' das funções dobrar e triplicar
```

### Quiz de Fixação
1. O que é necessário para que uma função seja considerada uma Closure?
   > **Resposta:** Ela deve ser uma função interna que referencia variáveis de uma função externa e é retornada por ela.
2. Como uma Closure ajuda na encapsulação de dados?
   > **Resposta:** Ela permite esconder variáveis dentro do escopo de uma função, tornando-as inacessíveis de fora, exceto através da função interna.
3. Se eu deletar a função externa (ex: `del criar_multiplicador`), a função `dobrar` para de funcionar?
   > **Resposta:** Não, pois ela capturou o valor necessário no momento da sua criação.

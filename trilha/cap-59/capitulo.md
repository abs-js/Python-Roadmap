# Capítulo 59: Name Mangling (`_` vs `__`) – O Segredo das Variáveis

### Teoria Sem Enrolação
No Python, não existe a palavra-chave `private` (como no Java ou C#). Tudo é um acordo entre cavalheiros. Mas existem convenções:
- **`_variavel` (Um underscore):** É um sinal de "Mantenha distância". Diz a outros programadores: "Isso é interno, use por sua conta e risco, mas eu posso mudar a qualquer momento".
- **`__variavel` (Dois underscores):** Ativa o **Name Mangling**. O Python muda o nome interno da variável para `_Classe__variavel`. Isso dificulta que uma subclasse acidentalmente sobrescreva esse atributo. É o mais próximo que chegamos de uma variável "privada".

### A Grande Analogia
Imagine que sua classe é uma **Casa Particular**.
- Um atributo sem underline é a **Varanda**: qualquer um vê e pode entrar.
- Um atributo com `_` é o **Quarto com a porta encostada**: você pode entrar, mas sabe que é um espaço íntimo e que não deveria estar ali sem ser convidado.
- Um atributo com `__` é o **Cofre escondido atrás do quadro**: ele não sumiu da casa, mas o Python mudou a "etiqueta" dele para que ninguém o encontre por acidente. Se você souber o segredo (o novo nome mangled), você ainda consegue abrir, mas dá muito mais trabalho.

### Desafio de Aplicação CLI: "O Sistema de Senha Super Protegido"
1. Crie uma classe `Segredo`.
2. Defina um atributo `__chave` no `__init__`.
3. Tente acessar `objeto.__chave` de fora da classe e veja o erro de atributo.
4. Tente acessar usando o nome "mangled" (`_Classe__chave`) e veja que o segredo é revelado.

### Gabarito do Desafio
```python
class Segredo:
    def __init__(self, valor):
        self.__chave = valor # Name Mangling ativado

cofre = Segredo("1234-AB")

try:
    print(cofre.__chave)
except AttributeError:
    print("Erro: Você não tem acesso direto à __chave!")

# Acessando via name mangling (o nome secreto que o Python criou)
print(f"Acesso 'hacker': {cofre._Segredo__chave}")
```

### Quiz de Fixação
1. O que acontece internamente com uma variável que começa com `__`?
   > **Resposta:** O Python renomeia ela para `_NomeDaClasse__nome_da_variavel`.
2. Qual a diferença de intenção entre usar um ou dois underscores antes de um nome?
   > **Resposta:** Um `_` é apenas um aviso de "uso interno"; dois `__` servem para evitar conflitos de nomes em herança (mangling).
3. O Python proíbe tecnicamente o acesso a variáveis com `__`?
   > **Resposta:** Não, ele apenas dificulta o acesso mudando o nome, mas o acesso ainda é possível.

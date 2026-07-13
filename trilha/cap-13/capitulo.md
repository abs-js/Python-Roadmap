# Capítulo 13: Módulos e Packages – O Kit de Ferramentas Externas

### Teoria Sem Enrolação
Você não precisa reinventar a roda. O Python vem com uma "Biblioteca Padrão" imensa e permite que você use códigos escritos por outras pessoas. 
- **`import modulo`**: Traz o kit inteiro para o seu código.
- **`from modulo import ferramenta`**: Traz apenas uma peça específica.
- **`as`**: Dá um apelido para o módulo (ex: `import pandas as pd`).
Módulos são arquivos `.py`. Packages são pastas contendo vários módulos.

### A Grande Analogia
Imagine que o Python básico é uma **Cozinha Vazia**. Você tem o fogão e a pia (os comandos básicos). 
Os **Módulos** são como **Eletrodomésticos Específicos** que você traz de fora: 
- Se você quer fazer um suco, você "importa" o liquidificador. 
- Se quer pesar comida, "importa" a balança (módulo `math`). 
- Se quer cronometrar o cozimento, "importa" o relógio (módulo `time`).
Você não precisa construir o liquidificador do zero; basta saber como ligar o botão de importar.

### Desafio de Aplicação CLI: "O Sorteador de Equipes"
Use o módulo nativo `random` para criar um programa que:
1. Tenha uma lista de 6 nomes de amigos.
2. Sorteie aleatoriamente um "Líder" do grupo.
3. Embaralhe a lista e divida os amigos em duas duplas.

### Gabarito do Desafio
```python
import random

amigos = ["Alice", "Bruno", "Caio", "Duda", "Elias", "Fernanda"]

# Sorteando um item aleatório
lider = random.choice(amigos)
print(f"O líder sorteado é: {lider}")

# Embaralhando a lista original
random.shuffle(amigos)

# Dividindo em duplas usando fatiamento de listas (slicing)
dupla1 = amigos[0:2]
dupla2 = amigos[2:4]

print(f"Dupla 1: {dupla1}")
print(f"Dupla 2: {dupla2}")
```

### Quiz de Fixação
1. Qual a diferença entre `import math` e `from math import sqrt`?
   > **Resposta:** O primeiro importa todas as funções do módulo (usa-se `math.sqrt()`), o segundo importa apenas a raiz quadrada (usa-se apenas `sqrt()`).
2. Como se chama um arquivo Python que pode ser importado por outro?
   > **Resposta:** Módulo.
3. Para que serve o comando `import random as rd`?
   > **Resposta:** Para importar o módulo `random` e dar a ele o apelido de `rd`, facilitando a escrita no código.

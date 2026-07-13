# Capítulo 2: Tipos de Dados - A Natureza da Informação

### Teoria Sem Enrolação
Nem toda informação é igual. O Python é "fortemente tipado", o que significa que ele se importa muito com o tipo de dado que você está usando. Os 4 pilares fundamentais são:
1.  **Inteiros (int):** Números sem casas decimais (10, -5, 0).
2.  **Flutuantes (float):** Números com casas decimais (10.5, 3.1415, -0.01). Importante: usamos **ponto** e não vírgula.
3.  **Strings (str):** Textos. Devem estar sempre entre aspas simples `'texto'` ou duplas `"texto"`.
4.  **Booleanos (bool):** O binário da vida. Só tem dois valores: `True` (Verdadeiro) ou `False` (Falso). Lembre-se: a primeira letra é sempre maiúscula.

### A Grande Analogia
Imagine que você está cozinhando. Você tem **ingredientes sólidos** (batatas = inteiros), **ingredientes líquidos** (leite = floats), **receitas escritas** (o papel da receita = strings) e o **interruptor do fogão** (ligado ou desligado = booleano). 
Você não pode "somar" uma batata com um parágrafo da receita. Tentar fazer `10 + "Bananas"` no Python causa uma pane porque ele sabe que você não deve misturar naturezas de dados diferentes sem o devido preparo.

### Desafio de Aplicação CLI: "Simulador de Status de RPG"
Você deve criar um sistema de status de um personagem de jogo. O programa deve definir:
- O nome do herói (Texto)
- O nível de força (Inteiro)
- A porcentagem de vida restante (Flutuante)
- Se o herói possui uma poção de mana (Booleano)

Depois, você deve imprimir o **tipo** de cada uma dessas variáveis usando a função `type()`.

### Gabarito do Desafio
```python
# Definindo os atributos do herói
nome_heroi = "Aragorn"
forca = 85
vida_percentual = 0.98 # Representa 98%
tem_pocao = False

# Exibindo os valores e seus tipos
print("Herói:", nome_heroi, "| Tipo:", type(nome_heroi))
print("Força:", forca, "| Tipo:", type(forca))
print("Vida:", vida_percentual, "| Tipo:", type(vida_percentual))
print("Tem Poção?", tem_pocao, "| Tipo:", type(tem_pocao))
```

### Quiz de Fixação
1. Se eu escrever `valor = "10"`, qual será o tipo dessa variável?
   > **Resposta:** String (str), porque o número está entre aspas.
2. Como o Python diferencia um número inteiro de um número decimal?
   > **Resposta:** Pela presença do ponto decimal (ex: 5 é int, 5.0 é float).
3. Qual função usamos para descobrir o tipo de uma variável?
   > **Resposta:** A função `type()`.

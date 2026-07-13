# Capítulo 75: Math e Statistics – A Calculadora Científica

### Teoria Sem Enrolação
Para cálculos simples, usamos `+` e `-`. Para matemática de verdade, usamos o módulo **`math`** e o **`statistics`**.
- **`math.ceil()` / `math.floor()`**: Arredonda para cima ou para baixo.
- **`math.sqrt()`**: Raiz quadrada.
- **`statistics.mean()` / `median()`**: Média e Mediana de uma lista de números.
Esses módulos são escritos em C, o que os torna absurdamente rápidos para processar volumes gigantescos de cálculos.

### A Grande Analogia
Imagine que o Python básico é o seu **Raciocínio Lógico**. Para saber quanto é 2+2, você usa a cabeça.
Mas o módulo `math` é como se você tirasse do bolso uma **Calculadora de Engenharia da HP**. Ela tem botões prontos para logaritmos, senos e raízes complexas que você levaria horas para calcular no papel. O módulo `statistics` é como ter um **Estatístico do IBGE** ao seu lado: você joga uma saca de números para ele, e ele te devolve o resumo da "saúde" desses dados em segundos.

### Desafio de Aplicação CLI: "O Analista de Desempenho de Vendas"
Crie um programa que receba uma lista de valores de vendas do mês.
1. Calcule a média das vendas usando `statistics`.
2. Encontre a maior venda.
3. Se a raiz quadrada da soma de todas as vendas for maior que 100, dê um bônus de "Destaque" para a equipe.

### Gabarito do Desafio
```python
import math
import statistics

vendas = [150.50, 200.00, 50.00, 300.75, 45.00]

media = statistics.mean(vendas)
total = sum(vendas)
raiz_total = math.sqrt(total)

print(f"Média de vendas: R$ {media:.2f}")
print(f"Total vendido: R$ {total:.2f}")
print(f"Indicador de Bônus (Raiz do Total): {raiz_total:.2f}")

if raiz_total > 100:
    print("STATUS: Equipe ganhou o Bônus de Destaque!")
else:
    print("STATUS: Metas não alcançadas para bônus.")
```

### Quiz de Fixação
1. Qual a diferença entre `round()` (nativo) e `math.ceil()`?
   > **Resposta:** `round()` arredonda para o mais próximo; `math.ceil()` sempre força o arredondamento para cima.
2. Qual função do módulo `statistics` encontra o valor central de uma lista ordenada?
   > **Resposta:** `statistics.median()`.
3. Como calculamos o fatorial de um número usando o módulo math?
   > **Resposta:** `math.fatorial(n)`.

# Capítulo 24: Datetime – O Senhor do Tempo

### Teoria Sem Enrolação
Lidar com datas e horas manualmente é perigoso (anos bissextos, fusos horários, meses com dias diferentes). O módulo `datetime` resolve isso.
- `datetime.now()`: Pega o momento exato agora.
- `timedelta`: É usado para fazer cálculos de tempo (somar 10 dias, subtrair 2 horas).
- `strptime`: Converte uma **String** em um objeto **Data** (String Parse Time).
- `strftime`: Converte um objeto **Data** em uma **String** formatada (String Format Time).

### A Grande Analogia
Pense no objeto `datetime` como um **Cronômetro Suíço Ultra Preciso**. 
Ele não guarda apenas um texto "10/05/2023"; ele entende o calendário inteiro. 
Se você perguntar ao cronômetro: "Que dia será daqui a 1 milhão de segundos?", ele faz o cálculo complexo (`timedelta`) e te entrega a resposta exata. 
O `strftime` é como escolher a **Máscara de Exibição**: você pode ver a hora no formato brasileiro (DD/MM), americano (MM/DD) ou até por extenso.

### Desafio de Aplicação CLI: "O Contador de Dias de Vida"
Crie um programa que:
1. Peça ao usuário sua data de nascimento (formato: DD/MM/AAAA).
2. Converta essa string em um objeto `datetime`.
3. Calcule quantos dias o usuário já viveu até hoje.
4. Informe se o dia atual é o aniversário dele.

### Gabarito do Desafio
```python
from datetime import datetime

data_str = input("Digite sua data de nascimento (DD/MM/AAAA): ")

# Convertendo string para data
nascimento = datetime.strptime(data_str, "%d/%m/%Y")
hoje = datetime.now()

# Calculando a diferença
diferenca = hoje - nascimento
dias_vividos = diferenca.days

print(f"Você já viveu aproximadamente {dias_vividos} dias!")

# Verificando aniversário
if nascimento.day == hoje.day and nascimento.month == hoje.month:
    print("PARABÉNS! Hoje é seu aniversário! 🎂")
```

### Quiz de Fixação
1. Qual classe usamos para representar uma duração ou intervalo de tempo?
   > **Resposta:** `timedelta`.
2. O que faz o código `data.strftime("%Y")`?
   > **Resposta:** Extrai apenas o ano (com 4 dígitos) de um objeto de data e o transforma em string.
3. Se eu quiser subtrair 1 semana de uma data, como devo proceder?
   > **Resposta:** `data_original - timedelta(weeks=1)`.

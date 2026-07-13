# Capítulo 3: Entrada e Saída (O Diálogo com o Usuário)

### Teoria Sem Enrolação
Um programa que não interage é apenas um monólogo. Para tornar as coisas dinâmicas, usamos:
-   **`print()`**: Envia dados para fora (saída).
-   **`input()`**: Recebe dados de fora (entrada).

**O Grande Pulo do Gato:** Todo dado capturado pelo `input()` chega ao Python como uma **String**. Se você pedir a idade do usuário e quiser fazer um cálculo matemático, precisará converter essa string para um inteiro. Isso se chama *Casting* ou *Conversão de Tipo*.
Exemplo: `idade = int(input("Digite sua idade: "))`.

### A Grande Analogia
Imagine o `print()` como um **megafone**: você grita uma informação para quem estiver na frente do computador. 
Já o `input()` é como uma **caixa de correio**: o programa para tudo o que está fazendo, coloca uma bandeirinha de espera e só continua quando alguém deposita uma carta (digita algo e aperta Enter).

### Desafio de Aplicação CLI: "Calculadora de Gorjetas Amigável"
Crie um programa que:
1. Pergunte o valor total da conta no restaurante.
2. Pergunte quantos amigos vão dividir a conta.
3. Calcule quanto cada um deve pagar (considerando que a conta já inclui os 10%).
4. Exiba uma mensagem personalizada com o valor para cada pessoa.

### Gabarito do Desafio
```python
# Entrada de dados (com conversão de tipo!)
valor_total = float(input("Qual o valor total da conta (R$)? "))
qtd_pessoas = int(input("Em quantas pessoas vão dividir? "))

# Processamento
valor_por_pessoa = valor_total / qtd_pessoas

# Saída de dados
print("--- DIVISÃO DA CONTA ---")
print("Valor total: R$", valor_total)
print("Cada um deve pagar: R$", valor_por_pessoa)
print("Obrigado por usar nosso sistema!")
```

### Quiz de Fixação
1. Qual o tipo de dado padrão retornado pela função `input()`?
   > **Resposta:** String (str).
2. O que acontece se eu tentar converter a string "Abacaxi" em um inteiro usando `int("Abacaxi")`?
   > **Resposta:** O Python gerará um Erro de Valor (`ValueError`), pois não há representação numérica para essa palavra.
3. Como você faria para imprimir duas variáveis na mesma linha usando um único `print()`?
   > **Resposta:** Separando as variáveis por vírgula dentro dos parênteses: `print(var1, var2)`.

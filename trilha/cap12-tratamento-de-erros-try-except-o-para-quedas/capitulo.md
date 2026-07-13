# Capítulo 12: Tratamento de Erros (Try/Except) – O Para-quedas

### Teoria Sem Enrolação
Erros acontecem. O usuário pode digitar "abc" onde deveria ser um número, ou o programa pode tentar dividir algo por zero. Se você não tratar isso, o programa "crash" (fecha sozinho).
- **`try` (tente):** Você coloca o código que "pode dar problema" aqui dentro.
- **`except` (exceto):** Se o erro ocorrer, o Python pula para cá em vez de fechar o programa.
- **`finally`:** (Opcional) Roda sempre, havendo erro ou não.

### A Grande Analogia
Imagine que você está em um **Trapézio de Circo**. 
O bloco `try` é o seu salto mortal. Se tudo der certo, você brilha. 
O bloco `except` é a **Rede de Proteção**. Se você escorregar ou errar o cálculo, você não morre (o programa não fecha); você cai suavemente na rede, se levanta e continua o espetáculo.

### Desafio de Aplicação CLI: "A Divisão À Prova de Erros"
Crie um programa que peça dois números ao usuário e realize a divisão do primeiro pelo segundo. O programa não pode travar se:
1. O usuário digitar um texto em vez de um número.
2. O usuário tentar dividir por zero.
Exiba mensagens de erro amigáveis para cada caso.

### Gabarito do Desafio
```python
try:
    num1 = float(input("Digite o dividendo: "))
    num2 = float(input("Digite o divisor: "))
    resultado = num1 / num2
    print(f"Resultado: {resultado}")

except ValueError:
    print("Erro: Por favor, digite apenas números válidos.")

except ZeroDivisionError:
    print("Erro: A matemática não permite divisão por zero!")

except Exception as erro:
    print(f"Ocorreu um erro inesperado: {erro}")

finally:
    print("Operação finalizada.")
```

### Quiz de Fixação
1. Qual o comando usado para capturar qualquer tipo de erro genérico?
   > **Resposta:** `except Exception:`.
2. O código dentro do bloco `finally` é executado se o `try` funcionar perfeitamente?
   > **Resposta:** Sim, o `finally` sempre é executado.
3. Posso ter vários blocos `except` para o mesmo `try`?
   > **Resposta:** Sim, um para cada tipo de erro específico que você queira tratar.

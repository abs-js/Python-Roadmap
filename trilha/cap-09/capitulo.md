# Capítulo 9: Estruturas de Repetição (While) – Condição em Movimento

### Teoria Sem Enrolação
Diferente do `for` (que percorre uma lista), o `while` (enquanto) repete um bloco de código **enquanto** uma condição for verdadeira.
- É ideal quando você **não sabe** quantas vezes a repetição vai acontecer (ex: esperar o usuário digitar a senha correta).
- **Cuidado:** Se a condição nunca se tornar falsa, você terá um "Loop Infinito", que trava o computador.
- **`break`:** Um comando de emergência para sair do loop imediatamente.

### A Grande Analogia
Imagine que você está enchendo uma **Piscina com Mangueira**.
Sua regra é: "**Enquanto** o nível da água for menor que 1.50m (capacidade máxima), continue com a mangueira ligada." 
Você não sabe se isso vai levar 10 minutos ou 2 horas (depende da pressão da água), mas você verifica a altura a cada segundo. Assim que atingir 1.50m, você para.

### Desafio de Aplicação CLI: "O Jogo de Adivinhação"
O programa deve definir um `numero_secreto = 7`. 
1. Use um `while` para pedir ao usuário que chute um número.
2. Se o usuário errar, diga "Tente novamente".
3. Se o usuário acertar, exiba "Você venceu!" e saia do loop.

### Gabarito do Desafio
```python
numero_secreto = 7
chute = 0 # Inicializamos com um valor diferente do segredo

print("--- DESAFIO DE ADIVINHAÇÃO ---")

while chute != numero_secreto:
    chute = int(input("Chute um número de 1 a 10: "))
    
    if chute != numero_secreto:
        print("Errou! Tente de novo...")

print("Parabéns! Você descobriu o número secreto.")
```

### Quiz de Fixação
1. Qual o perigo de usar uma condição que nunca muda para `False` no `while`?
   > **Resposta:** Gerar um loop infinito e travar a execução do programa.
2. Como podemos forçar a saída de qualquer loop (for ou while) antes do tempo?
   > **Resposta:** Usando a palavra-chave `break`.
3. Qual estrutura é melhor para percorrer uma lista: `for` ou `while`?
   > **Resposta:** O `for`, pois já é desenhado para iterar sobre coleções de forma limpa.

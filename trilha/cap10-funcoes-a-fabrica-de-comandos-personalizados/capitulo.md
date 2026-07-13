# Capítulo 10: Funções – A Fábrica de Comandos Personalizados

### Teoria Sem Enrolação
Até agora, você escreveu códigos que rodam de cima para baixo. Mas e se você precisasse usar o mesmo cálculo 50 vezes em partes diferentes do programa? Em vez de copiar e colar, você cria uma **Função**.
- **`def`**: É a palavra que avisa ao Python: "Vou definir uma função agora".
- **Parâmetros**: São as informações que a função precisa receber para trabalhar (os ingredientes).
- **`return`**: É o resultado que a função devolve para quem a chamou. 

Uma função é como um "atalho". Depois de definida, você a invoca pelo nome, ex: `calcular_media()`.

### A Grande Analogia
Pense na função como uma **Máquina de Café**. 
Você não precisa construir a lógica de aquecer a água e moer o grão toda vez que quer beber. A máquina é a função `fazer_cafe()`. 
- Os **parâmetros** seriam: o tipo do grão e a quantidade de açúcar. 
- O **processo interno** (esquentar, filtrar) você define apenas uma vez dentro da máquina.
- O **return** é a xícara cheia de café pronta para ser consumida por você.

### Desafio de Aplicação CLI: "O Conversora de Temperaturas"
Crie uma função chamada `converter_para_celsius` que recebe uma temperatura em Fahrenheit e retorna o valor em Celsius. O programa principal deve pedir o valor ao usuário, chamar a função e exibir o resultado.
*Dica: A fórmula é `C = (F - 32) * 5/9`.*

### Gabarito do Desafio
```python
# Definindo a fábrica de conversão
def converter_para_celsius(fahrenheit):
    celsius = (fahrenheit - 32) * 5/9
    return celsius

# Programa Principal
temp_f = float(input("Digite a temperatura em Fahrenheit: "))

# Chamando a função e guardando o retorno numa variável
resultado = converter_para_celsius(temp_f)

print(f"A temperatura convertida é {resultado:.2f}°C")
```

### Quiz de Fixação
1. Qual a palavra-chave usada para enviar um valor de volta para fora da função?
   > **Resposta:** `return`.
2. O que acontece se uma função for definida mas nunca "chamada" no código?
   > **Resposta:** Nada. O código dentro dela nunca será executado.
3. Posso criar uma função que não recebe nenhum parâmetro?
   > **Resposta:** Sim, basta deixar os parênteses vazios, ex: `def saudar():`.

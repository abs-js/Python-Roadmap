# Capítulo 5: Condicionais (if, elif, else) - O Labirinto de Decisões

### Teoria Sem Enrolação
Até agora, seu código era uma linha reta. Com as **Condicionais**, criamos bifurcações.
- **`if` (se):** A porta de entrada. Se a condição for real, o código entra aqui.
- **`elif` (senão se):** Se a primeira porta estava fechada, tente esta. Você pode ter quantos quiser.
- **`else` (senão):** O caminho padrão. Se nenhuma das condições anteriores foi atendida, ele cai aqui.

**A Regra Sagrada: Identação.** No Python, você não usa chaves `{}` para fechar blocos. Você usa o **espaço (TAB)**. Se o código estiver alinhado para a direita, ele pertence ao `if`. Se estiver na margem esquerda, está fora.

### A Grande Analogia
Imagine que você é um **segurança de balada**. 
Sua instrução é: 
- `if`: Se a pessoa tiver mais de 18 anos, ela entra.
- `elif`: Se ela tiver exatamente 18 e estiver com um convite VIP, ela entra.
- `else`: Caso contrário, mande-a para casa.
A condição é o seu critério de avaliação; o bloco de código identado é a ação que você toma.

### Desafio de Aplicação CLI: "O Simulador de Radar de Trânsito"
Escreva um programa que peça a velocidade de um carro. 
- Se a velocidade for menor que 80km/h, exiba: "Direção Segura".
- Se for entre 80km/h e 100km/h, exiba: "Atenção: Você foi multado em R$ 130,00".
- Se for acima de 100km/h, exiba: "PERIGO: Multa Grave de R$ 800,00 e apreensão da CNH!".

### Gabarito do Desafio
```python
velocidade = float(input("Qual a velocidade atual do veículo (km/h)? "))

if velocidade < 80:
    print("Direção Segura. Continue assim!")
elif velocidade >= 80 and velocidade <= 100:
    print("Atenção: Você foi multado em R$ 130,00.")
else:
    print("PERIGO: Multa Grave de R$ 800,00 e apreensão da CNH!")
```

### Quiz de Fixação
1. O que acontece se eu esquecer de dar o "TAB" (espaço) na linha abaixo de um `if`?
   > **Resposta:** O Python exibirá um erro de identação (`IndentationError`) e o programa não funcionará.
2. Posso usar um `else` sem ter usado um `if` antes?
   > **Resposta:** Não. O `else` é sempre o final de uma estrutura iniciada por um `if`.
3. Qual a diferença entre `if` e `elif`?
   > **Resposta:** O `if` abre uma nova verificação independente; o `elif` só é testado se o `if` anterior for falso.

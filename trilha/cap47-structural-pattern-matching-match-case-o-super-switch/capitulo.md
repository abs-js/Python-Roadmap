# Capítulo 47: Structural Pattern Matching (match-case) – O Super Switch

### Teoria Sem Enrolação
Lançado no Python 3.10, o `match-case` não é apenas um "Switch" de outras linguagens. Ele permite o pareamento de padrões complexos.
- Ele pode desestruturar listas, dicionários e até objetos.
- Você pode usar o `_` como um "caso padrão" (wildcard).
- Você pode colocar condições (`if`) dentro dos casos, chamadas de "guards".

### A Grande Analogia
Imagine um **Separador Automático de Lixo**.
O sistema antigo (`if/elif`) olhava um item e perguntava: "É plástico?", "É metal?". 
O `match-case` é um **Portal com Molduras**: você joga o objeto lá dentro. Se ele tiver o formato exato de uma garrafa PET (uma lista com 2 itens, sendo o primeiro 'pet'), ele cai no cesto certo. Se ele tiver o formato de uma lata de alumínio escrito "Vazia", ele cai em outro. Ele reconhece a **estrutura** e o **conteúdo** do dado simultaneamente.

### Desafio de Aplicação CLI: "O Comandante de Robô"
Crie um sistema que recebe uma lista como comando.
1. Se a lista for `["mover", "frente"]`, imprima "Andando...".
2. Se a lista for `["mover", "tras", passos]`, imprima "Recuando [passos] metros".
3. Se for qualquer outra coisa, imprima "Comando desconhecido".

### Gabarito do Desafio
```python
def processar_comando(comando):
    match comando:
        case ["mover", "frente"]:
            print("Robô andando para frente.")
        
        case ["mover", "tras", int(passos)]:
            print(f"Robô recuando {passos} metros.")
            
        case ["parar"] | ["desligar"]: # Uso do OR (|)
            print("Robô parando...")
            
        case _: # Caso padrão
            print("Erro: Comando não reconhecido ou formato inválido.")

# Testes
processar_comando(["mover", "frente"])
processar_comando(["mover", "tras", 10])
processar_comando(["voar"])
```

### Quiz de Fixação
1. O `match-case` está disponível em qual versão do Python?
   > **Resposta:** 3.10 ou superior.
2. O que representa o símbolo `_` no final de um bloco `match`?
   > **Resposta:** O caso genérico (default) que captura qualquer coisa que não tenha casado com os padrões anteriores.
3. Posso capturar o valor de uma parte do padrão para usar dentro do case?
   > **Resposta:** Sim, como vimos no exemplo `["mover", "tras", passos]`, a variável `passos` é preenchida automaticamente.

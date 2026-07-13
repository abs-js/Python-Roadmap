# Capítulo 70: Introspecção e Módulo Inspect – Olhando Sob o Capô

### Teoria Sem Enrolação
A **Introspecção** é a capacidade de um programa de examinar as propriedades de seus próprios objetos em tempo de execução. O módulo **`inspect`** leva isso ao próximo nível.
- Você pode perguntar ao Python: "Quais são os argumentos que esta função recebe?", "Qual o código-fonte dessa função?" ou "Em qual arquivo essa classe foi definida?".
- É fundamental para criar ferramentas que geram documentação automática ou validam códigos de outros desenvolvedores.

### A Grande Analogia
Imagine que você está diante de um **Mecanismo de Relógio Blindado**.
Programar comum é apenas olhar os ponteiros girando. Usar o módulo **Inspect** é como ter um **Raio-X**. Você aponta para o relógio e consegue ver as engrenagens internas, quantas peças ele tem, quem fabricou cada parafuso e como elas se encaixam, tudo isso sem precisar abrir a caixa do relógio ou parar o tempo.

### Desafio de Aplicação CLI: "O Analisador de Funções Misteriosas"
Crie uma função simples `soma(a, b=10)`. 
1. Use o módulo `inspect` para descobrir o nome da função.
2. Use `inspect.signature` para listar o nome dos parâmetros e quais deles têm valores padrão.

### Gabarito do Desafio
```python
import inspect

def calcular_bonus(salario, multiplicador=1.5):
    return salario * multiplicador

# 1. Pegando a assinatura da função
assinatura = inspect.signature(calcular_bonus)

print(f"Analisando a função: {calcular_bonus.__name__}")

# 2. Percorrendo os parâmetros
for nome, param in assinatura.parameters.items():
    print(f"Parâmetro: {nome}")
    if param.default is not inspect.Parameter.empty:
        print(f"  - Valor padrão detectado: {param.default}")
    else:
        print(f"  - Este parâmetro é obrigatório.")
```

### Quiz de Fixação
1. O que significa "Introspecção" em programação?
   > **Resposta:** A capacidade do código de analisar a si próprio (objetos, classes, funções) durante a execução.
2. Como pegamos o código-fonte de uma função via Python?
   > **Resposta:** Usando o método `inspect.getsource(funcao)`.
3. Qual o objetivo de usar `inspect.signature()`?
   > **Resposta:** Obter informações detalhadas sobre os parâmetros, anotações de tipo e valores padrão de uma função ou método.

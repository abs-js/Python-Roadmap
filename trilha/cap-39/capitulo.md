# Capítulo 39: Design Patterns (Singleton) — O Highlander do Código

### Teoria Sem Enrolação
Design Patterns são soluções consagradas para problemas comuns de arquitetura. O **Singleton** é um dos mais famosos. Ele garante que uma classe tenha **uma, e apenas uma**, instância em todo o programa. É muito usado para gerenciar conexões de bancos de dados ou configurações globais, onde você não quer ter 10 objetos diferentes fazendo a mesma coisa e gastando memória.

### A Grande Analogia
Imagine o **Presidente de um País**. 
O país pode ter milhões de cidadãos, mas em qualquer momento do tempo, a função "Presidente" só pode ser ocupada por **uma única pessoa física**. Se você tentar "instanciar" um novo presidente, o sistema deve te devolver a referência daquele que já está no cargo. Existe apenas um ponto de controle central.

### Desafio de Aplicação CLI: "O Gerenciador de Configurações"
Crie uma classe chamada `Configuracao`. 
1. Use o método mágico `__new__` para garantir que, não importa quantas vezes você chame `Configuracao()`, ele sempre retorne a mesma instância (o mesmo endereço de memória).
2. Adicione um atributo `tema` e mude-o em um objeto, vendo que ele mudou automaticamente em "todos" os outros.

### Gabarito do Desafio
```python
class Configuracao:
    _instancia = None

    def __new__(cls):
        # Se ainda não existe uma instância, cria uma
        if cls._instancia is None:
            print("Criando instância única do sistema...")
            cls._instancia = super().__new__(cls)
            cls._instancia.tema = "Claro" # Atributo padrão
        return cls._instancia

# Testando o Singleton
conf1 = Configuracao()
conf2 = Configuracao()

print(f"ID conf1: {id(conf1)} | ID conf2: {id(conf2)}")

conf2.tema = "Escuro"
print(f"Tema no conf1: {conf1.tema}") # Mudou para Escuro também!
```

### Quiz de Fixação
1. Qual método mágico é responsável pela criação do objeto e é ideal para implementar o Singleton?
   > **Resposta:** `__new__`.
2. Qual a principal vantagem do padrão Singleton em relação a variáveis globais?
   > **Resposta:** Ele oferece encapsulamento, organização dentro de uma classe e controle sobre o momento da criação (Lazy Initialization).
3. O Singleton é recomendado para qualquer situação?
   > **Resposta:** Não. Se usado excessivamente, ele pode dificultar os testes unitários e esconder dependências entre as partes do código.

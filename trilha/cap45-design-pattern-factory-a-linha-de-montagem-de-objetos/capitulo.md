# Capítulo 45: Design Pattern: Factory – A Linha de Montagem de Objetos

### Teoria Sem Enrolação
O padrão **Factory** (Fábrica) é usado para centralizar a criação de objetos. Em vez de o seu programa principal ter que saber qual classe instanciar (o que gera dependência), ele pede para uma "Fábrica" criar o objeto para ele, baseando-se em uma string ou parâmetro. 
Isso mantém o código limpo: se você adicionar um novo tipo de objeto, só precisa mexer na fábrica, não no programa inteiro.

### A Grande Analogia
Imagine que você está em um **Totem de Autoatendimento do McDonald's**. 
Você não vai até a cozinha explicar como fritar a carne ou montar o pão. Você interage com o **Totem (a Fábrica)** e aperta o botão "Big Mac". O totem sabe qual "classe" de sanduíche deve mandar a cozinha preparar. Para você, o que importa é que o resultado final seja um sanduíche que "se alimenta", não importa a engenharia por trás da criação dele.

### Desafio de Aplicação CLI: "O Sistema de Notificações Multi-Plataforma"
1. Crie uma classe `SMS` e uma classe `Email`, ambas com um método `enviar(mensagem)`.
2. Crie uma classe `NotificacaoFactory` com um método estático que recebe a string "sms" ou "email" e retorna o objeto correto.
3. Peça ao usuário qual via ele prefere e envie uma mensagem usando a fábrica.

### Gabarito do Desafio
```python
class Email:
    def enviar(self, msg):
        print(f"Enviando E-mail: {msg}")

class SMS:
    def enviar(self, msg):
        print(f"Enviando SMS: {msg}")

class NotificacaoFactory:
    @staticmethod
    def criar_notificacao(tipo):
        if tipo == "email":
            return Email()
        elif tipo == "sms":
            return SMS()
        return None

# Programa Principal
servico = input("Deseja receber via (email/sms)? ").lower()
fabrica = NotificacaoFactory()
comunicador = fabrica.criar_notificacao(servico)

if comunicador:
    comunicador.enviar("Sua encomenda chegou!")
else:
    print("Tipo de notificação inválido.")
```

### Quiz de Fixação
1. Qual é o maior benefício do padrão Factory?
   > **Resposta:** Reduzir o acoplamento do código, isolando a lógica de criação dos objetos da lógica de uso deles.
2. Onde a lógica de "escolha" de qual classe usar deve ficar nesse padrão?
   > **Resposta:** Dentro do método da classe Factory.
3. Por que o método de uma Factory geralmente é um `@staticmethod`?
   > **Resposta:** Porque a fábrica não precisa guardar dados do estado (self); ela apenas executa a lógica de criação e entrega o resultado.

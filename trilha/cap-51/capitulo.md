# Capítulo 51: Networking – Sockets e a Conversa entre Máquinas

### Teoria Sem Enrolação
A internet nada mais é do que computadores trocando mensagens. O nível mais baixo dessa comunicação em Python é o módulo **`socket`**.
- Um socket é o ponto final de uma via de comunicação bidirecional.
- **Servidor:** Fica ouvindo (`listen`) em uma porta específica (ex: 8080) aguardando alguém ligar.
- **Cliente:** Inicia a conexão (`connect`) para o IP e Porta do servidor.
- Eles trocam dados através de **Bytes** (você precisa dar `.encode()` no texto para enviar e `.decode()` ao receber).

### A Grande Analogia
Imagine que o IP é o **Endereço do Prédio** e a Porta é o **Número do Apartamento**.
- O Servidor é o morador que fica em casa esperando o telefone tocar. Quando toca, ele atende (`accept`) e começa a conversar.
- O Cliente é quem disca o número.
- O cabo do telefone é o **Socket**. No entanto, eles falam línguas diferentes, então usam um **Tradutor de Código Morse (Encoding)** para garantir que as letras cheguem do outro lado corretamente pelo fio.

### Desafio de Aplicação CLI: "O Mensageiro de Eco (Echo Server)"
Este desafio exige dois scripts (ou rodar um após o outro):
1. Crie um servidor que receba uma mensagem, imprima no console e envie a mesma mensagem de volta para o cliente (em maiúsculas).
2. O servidor deve rodar em `localhost` e na porta `12345`.

### Gabarito do Desafio (Código do Servidor)
```python
import socket

# Configurando o Servidor
servidor = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
servidor.bind(('localhost', 12345))
servidor.listen(1)

print("Servidor aguardando conexão na porta 12345...")

conexao, endereco = servidor.accept()
print(f"Conectado por: {endereco}")

while True:
    # Recebendo 1024 bytes
    dados = conexao.recv(1024)
    if not dados:
        break
    
    mensagem = dados.decode('utf-8')
    print(f"Cliente disse: {mensagem}")
    
    # Respondendo (Echo)
    conexao.sendall(mensagem.upper().encode('utf-8'))

conexao.close()
```

### Quiz de Fixação
1. O que o método `bind()` faz em um socket de servidor?
   > **Resposta:** Ele associa o socket a um endereço IP e uma porta específica.
2. Por que precisamos usar `.encode()` antes de enviar uma string pelo socket?
   > **Resposta:** Porque sockets transmitem bytes brutos, e não objetos de texto (strings) do Python.
3. Qual o significado de `localhost` ou o IP `127.0.0.1`?
   > **Resposta:** É o endereço de "loopback", que aponta para o seu próprio computador.

# Capítulo 53: Hashlib – A Impressão Digital Digital (Segurança)

### Teoria Sem Enrolação
Em segurança da informação, você nunca deve salvar a senha real do usuário no banco de dados. Em vez disso, salvamos o **Hash**.
Um Hash é um algoritmo que transforma qualquer dado (uma palavra ou um livro inteiro) em uma sequência fixa de letras e números.
- **Unidirecional:** Você consegue gerar o hash a partir da senha, mas é impossível (matematicamente) descobrir a senha a partir do hash.
- **Determinístico:** A mesma senha sempre gerará o mesmo hash.
- **Efeito Avalanche:** Se você mudar uma única letra na senha, o hash muda completamente.

### A Grande Analogia
Imagine que o Hash é o **DNA de uma Pessoa**. 
A partir de um fio de cabelo, você consegue extrair o DNA. O DNA identifica a pessoa de forma única, mas você não consegue "reconstruir" a pessoa inteira de carne e osso apenas olhando para a sequência genética escrita em um papel. 
Se você quer saber se alguém é quem diz ser, você tira o DNA da pessoa de novo e compara com o DNA que você tem guardado no seu arquivo (o banco de dados). Se os códigos baterem, a pessoa é a mesma.

### Desafio de Aplicação CLI: "O Cofre de Senhas Simples"
Crie um programa que:
1. Peça ao usuário para cadastrar uma "Senha Mestra".
2. Gere o hash dessa senha usando o algoritmo `SHA-256` (do módulo `hashlib`) e guarde em uma variável.
3. Peça para o usuário digitar a senha novamente para "abrir o cofre".
4. Verifique se o hash da nova entrada bate com o hash guardado.

### Gabarito do Desafio
```python
import hashlib

# 1. Cadastro
senha_real = input("Cadastre sua senha mestra: ")
# O hashlib precisa que o texto seja convertido em bytes (.encode())
hash_cadastro = hashlib.sha256(senha_real.encode()).hexdigest()

print("\n--- COFRE TRANCADO ---")

# 2. Verificação
tentativa = input("Digite sua senha para entrar: ")
hash_tentativa = hashlib.sha256(tentativa.encode()).hexdigest()

if hash_tentativa == hash_cadastro:
    print("Acesso concedido! Bem-vindo ao cofre.")
else:
    print("Senha incorreta! O sistema foi bloqueado.")
```

### Quiz de Fixação
1. O que significa dizer que um hash é "unidirecional"?
   > **Resposta:** Que não é possível reverter o processo para obter o dado original a partir do código gerado.
2. Por que usamos `.hexdigest()` ao gerar um hash?
   > **Resposta:** Para obter o resultado em um formato amigável de string (hexadecimal), em vez de bytes puros.
3. Se eu gerar o hash da palavra "Python" hoje e gerar novamente amanhã, o resultado será o mesmo?
   > **Resposta:** Sim, os algoritmos de hash são determinísticos.

# Capítulo 32: Variáveis de Ambiente e .env – O Cofre de Segredos

### Teoria Sem Enrolação
Nunca, jamais, coloque senhas de banco de dados ou chaves de API diretamente no seu código. Se você subir esse código para o GitHub, qualquer um terá acesso aos seus segredos. 
Usamos **Variáveis de Ambiente** para guardar esses dados sensíveis fora do código:
1. Criamos um arquivo chamado `.env` no computador.
2. Colocamos lá: `API_KEY=minhasenha123`.
3. No Python, usamos o módulo `os` ou a biblioteca `python-dotenv` para ler esse valor. 
Assim, o código fica limpo e os segredos ficam protegidos no ambiente do servidor.

### A Grande Analogia
Imagine que você tem um **Diário Secreto com Cadeado**. 
O código do seu programa é o texto do diário. Se você escrever a combinação do cadeado na primeira página do diário, o cadeado não serve para nada. 
As **Variáveis de Ambiente** são como você guardar a combinação em um **Papelzinho no seu Bolso**. Quem ler o diário (o código) verá apenas uma instrução: "Para abrir, use a combinação que está no bolso do autor". O segredo está com você (no ambiente), não no papel (no código).

### Desafio de Aplicação CLI: "O Simulador de Login Seguro"
Crie um pequeno script que tente ler um segredo chamado `TOKEN_ACESSO`.
1. Se a variável de ambiente existir, exiba "Acesso concedido ao sistema!".
2. Se não existir, exiba "ERRO: Token de segurança não encontrado!".
*(Dica: Você pode definir uma variável de ambiente no seu terminal antes de rodar o script ou usar o módulo `os.environ`).*

### Gabarito do Desafio
```python
import os

# Simulando a leitura de uma variável de ambiente
# O método .get evita que o programa trave caso a variável não exista
token = os.environ.get("TOKEN_ACESSO")

if token:
    print(f"Token '{token}' detectado. Acesso concedido!")
else:
    print("ACESSO NEGADO: Configure a variável de ambiente TOKEN_ACESSO.")

# Para testar no terminal (Linux/Mac): export TOKEN_ACESSO=123 && python script.py
# No Windows (CMD): set TOKEN_ACESSO=123 && python script.py
```

### Quiz de Fixação
1. Por que não devemos commitar arquivos `.env` no Git/GitHub?  
   > **Resposta:** Porque eles contêm informações sensíveis e secretas que não devem ser públicas.
2. Qual módulo nativo do Python permite acessar variáveis de ambiente?  
   > **Resposta:** O módulo `os` (usando `os.environ`).
3. Qual a vantagem de usar `os.environ.get("NOME")` em vez de `os.environ["NOME"]`?  
   > **Resposta:** O `.get()` retorna `None` se a variável não existir, enquanto os colchetes causam um erro de chave (`KeyError`).

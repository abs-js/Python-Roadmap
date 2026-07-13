# Capítulo 20: Expressões Regulares (Regex) – O Scanner de Padrões

### Teoria Sem Enrolação
Expressões Regulares (módulo `re`) são como uma linguagem de busca ultra-poderosa dentro de textos. Em vez de procurar por uma palavra exata, você procura por um **padrão**.
- `\d`: Representa qualquer dígito (0-9).
- `\w`: Representa letras e números.
- `+`: Significa "um ou mais".
- `[a-z]`: Define um intervalo de letras.
Isso é essencial para validar e-mails, telefones, CPFs ou extrair links de sites.

### A Grande Analogia
Imagine que você tem uma **Pilha de 10.000 Cartas** e precisa encontrar todos os números de telefone. 
Fazer isso manualmente usando `if "1" in texto` é impossível. 
O Regex é como um **Scanner de Raio-X Programável**. Você configura o scanner para: "Procure algo que tenha (dois números) entre parênteses, seguido de cinco números, um traço e mais quatro números". Você passa o scanner na pilha e ele acende uma luz vermelha exatamente onde o padrão foi encontrado.

### Desafio de Aplicação CLI: "O Validador de Senhas Fortes"
Use o módulo `re` para verificar se uma senha digitada pelo usuário é válida. Os critérios são:
1. Deve ter pelo menos um número.
2. Deve ter pelo menos uma letra maiúscula.
3. Deve ter no mínimo 6 caracteres.

### Gabarito do Desafio
```python
import re

def validar_senha(senha):
    if len(senha) < 6:
        return "Erro: Mínimo de 6 caracteres."
    
    # re.search procura o padrão em qualquer lugar da string
    if not re.search(r"\d", senha): # \d = dígito
        return "Erro: A senha deve conter pelo menos um número."
    
    if not re.search(r"[A-Z]", senha): # [A-Z] = letra maiúscula
        return "Erro: A senha deve conter pelo menos uma letra maiúscula."
    
    return "Senha forte! Acesso permitido."

# Teste
sua_senha = input("Digite uma nova senha: ")
print(validar_senha(sua_senha))
```

### Quiz de Fixação
1. No Regex, o que o símbolo `\d` representa?
   > **Resposta:** Qualquer dígito numérico de 0 a 9.
2. Qual função do módulo `re` usamos para encontrar todas as ocorrências de um padrão em um texto?
   > **Resposta:** `re.findall()`.
3. Para que serve o prefixo `r` antes das aspas em um padrão Regex (ex: `r"\d"`)?
   > **Resposta:** Significa "Raw String" (string bruta), garantindo que o Python não interprete as barras invertidas como comandos especiais.

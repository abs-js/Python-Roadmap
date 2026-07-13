# Capítulo 14: Manipulação de Arquivos – A Memória Persistente

### Teoria Sem Enrolação
Tudo o que fizemos até agora "morria" quando o programa fechava. Para salvar dados para sempre, usamos arquivos.
- **`open("arquivo.txt", "modo")`**: Abre o arquivo. Modos comuns: `r` (leitura), `w` (escrita - apaga o que tinha), `a` (append - adiciona ao final).
- **O comando `with`**: É a forma moderna e segura de abrir arquivos. Ele garante que o arquivo seja fechado automaticamente, mesmo se o programa der erro.

### A Grande Analogia
Imagine que o seu programa é uma **Pessoa com Alzheimer**. Ela conversa muito bem, mas esquece tudo quando dorme. 
Escrever em um arquivo é como dar a essa pessoa um **Caderno de Anotações**. 
Antes de dormir (fechar o programa), ela escreve os dados importantes. Ao acordar (iniciar o programa), a primeira coisa que ela faz é ler o caderno para recuperar a memória.

### Desafio de Aplicação CLI: "O Diário Digital"
Crie um programa que:
1. Peça ao usuário para digitar uma frase que represente o seu dia.
2. Salve essa frase em um arquivo chamado `diario.txt` sem apagar o conteúdo anterior.
3. Em seguida, leia o arquivo inteiro e exiba todas as memórias salvas no console.

### Gabarito do Desafio
```python
# Escrevendo no arquivo (modo 'a' de append)
mensagem = input("Como foi seu dia hoje? ")

with open("diario.txt", "a", encoding="utf-8") as arquivo:
    arquivo.write(mensagem + "\n")

print("\n--- LENDO SEU DIÁRIO ---")

# Lendo o arquivo (modo 'r' de read)
with open("diario.txt", "r", encoding="utf-8") as arquivo:
    conteudo = arquivo.read()
    print(conteudo)
```

### Quiz de Fixação
1. O que acontece se eu abrir um arquivo no modo `"w"` e ele já contiver texto?
   > **Resposta:** Todo o conteúdo anterior será apagado e substituído pelo novo.
2. Por que é recomendado usar o bloco `with` em vez de apenas `open()` e `close()`?
   > **Resposta:** Porque o `with` gerencia o fechamento do arquivo automaticamente, evitando corrupção de dados e vazamento de memória.
3. Qual modo de abertura devo usar para apenas adicionar informações ao final de um arquivo?
   > **Resposta:** O modo `"a"` (append).

# Capítulo 50: SQLite3 – O Banco de Dados de Bolso

### Teoria Sem Enrolação
Guardar dados em TXT ou JSON é legal, mas não escala. Para organizar dados de forma profissional, usamos SQL. O Python já vem com o **SQLite3**, um banco de dados completo que não precisa de servidor: ele salva tudo em um único arquivo `.db`.
- **Conexão:** Você "liga" para o banco.
- **Cursor:** É o seu "braço" dentro do banco que executa os comandos.
- **Commit:** Salva as alterações (importante: se não der commit, as mudanças somem!).
- **Comandos:** `CREATE TABLE`, `INSERT`, `SELECT`, `UPDATE`, `DELETE`.

### A Grande Analogia
Imagine que o SQLite é um **Arquivo de Aço de um Escritório Antigo**.
- O arquivo de aço é o seu ficheiro `.db`.
- O **Cursor** é o seu **Secretário**. Você não entra no arquivo; você entrega um bilhetinho escrito em SQL para o secretário.
- O secretário vai até as gavetas, procura as fichas, altera o que precisa ou traz as informações de volta para você.
- O **Commit** é o ato de **Trancar a Gaveta com Chave**. Se o prédio pegar fogo (o programa cair) antes de você trancar, o secretário larga as fichas no chão e tudo o que foi feito é perdido.

### Desafio de Aplicação CLI: "A Agenda de Contatos Persistente"
Crie um programa que:
1. Crie uma tabela `contatos` com as colunas `nome` e `telefone`.
2. Peça ao usuário o nome e telefone de um amigo e salve no banco.
3. Recupere todos os contatos salvos e os exiba no console de forma organizada.

### Gabarito do Desafio
```python
import sqlite3

# Conectando (Cria o arquivo se não existir)
conexao = sqlite3.connect("minha_agenda.db")
cursor = conexao.cursor()

# Criando a tabela
cursor.execute("""
CREATE TABLE IF NOT EXISTS contatos (
    nome TEXT,
    telefone TEXT
)
""")

# Inserindo dados
nome = input("Digite o nome: ")
fone = input("Digite o telefone: ")

cursor.execute("INSERT INTO contatos (nome, telefone) VALUES (?, ?)", (nome, fone))
conexao.commit() # Salvando no disco!

# Lendo dados
print("\n--- SEUS CONTATOS ---")
cursor.execute("SELECT * FROM contatos")
for linha in cursor.fetchall():
    print(f"Nome: {linha[0]} | Tel: {linha[1]}")

conexao.close()
```

### Quiz de Fixação
1. O que acontece se você executar um comando `INSERT` mas esquecer de chamar o método `commit()`?
   > **Resposta:** Os dados serão inseridos apenas na memória temporária e serão perdidos assim que a conexão for fechada.
2. Por que usamos `?` na query em vez de f-strings (Ex: `values (?, ?)` vs `values ({nome})`)?
   > **Resposta:** Para prevenir ataques de **SQL Injection**, uma vulnerabilidade de segurança grave onde o usuário pode injetar comandos maliciosos no banco.
3. Qual método usamos para pegar todos os resultados de uma consulta `SELECT`?
   > **Resposta:** O método `fetchall()`.

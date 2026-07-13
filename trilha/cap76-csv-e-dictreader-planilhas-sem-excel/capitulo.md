# Capítulo 76: CSV e DictReader – Planilhas sem Excel

### Teoria Sem Enrolação
O CSV (Comma Separated Values) é o formato mais comum para troca de dados entre sistemas. O módulo **`csv`** do Python permite ler esses arquivos como se fossem listas ou, melhor ainda, como **Dicionários**.
- **`DictReader`**: Transforma cada linha do arquivo em um dicionário, onde a chave é o nome da coluna no topo da planilha. Isso torna o código muito mais legível.

### A Grande Analogia
Imagine que um arquivo CSV é uma **Lista de Compras em um Varal**. 
Cada linha é uma peça de roupa pendurada. O **`DictReader`** é um sistema que coloca uma **Etiqueta** em cada detalhe da roupa. Em vez de você dizer "pegue a terceira informação da segunda peça", você simplesmente diz "me dê o PREÇO da CAMISA". Você para de contar colunas e passa a chamar os dados pelos nomes deles.

### Desafio de Aplicação CLI: "O Importador de Produtos"
(Simularemos o conteúdo de um arquivo CSV).
1. Dado o conteúdo: `nome,preco,estoque\nTeclado,150,5\nMouse,80,10`.
2. Use `csv.DictReader` para ler esses dados.
3. Imprima uma frase para cada produto: "Temos [estoque] unidades de [nome] custando R$[preco]".

### Gabarito do Desafio
```python
import csv
import io

# Simulando um arquivo CSV na memória
conteudo_csv = "nome,preco,estoque\nTeclado,150,10\nMouse,80,20\nMonitor,900,5"
arquivo_fake = io.StringIO(conteudo_csv)

# Usando DictReader para facilitar a vida
leitor = csv.DictReader(arquivo_fake)

print("--- RELATÓRIO DE ESTOQUE ---")
for linha in leitor:
    # Acessamos os dados pelos nomes das colunas!
    print(f"Temos {linha['estoque']} unidades de {linha['nome']} custando R$ {linha['preco']}")
```

### Quiz de Fixação
1. Qual a vantagem do `DictReader` sobre o `reader` comum do módulo CSV?
   > **Resposta:** O `DictReader` permite acessar as colunas pelo nome (header), tornando o código menos suscetível a erros se a ordem das colunas mudar.
2. O que significa a sigla CSV?
   > **Resposta:** Comma Separated Values (Valores Separados por Vírgula).
3. Como você especificaria um separador diferente, como ponto e vírgula `;`?
   > **Resposta:** Usando o argumento `delimiter=';'` na função de leitura.

---

**AVISO IMPORTANTE:** 
Com esses capítulos, cobrimos **todos os fundamentos, bibliotecas padrão essenciais e conceitos avançados** previstos no Roadmap de Python Core (Linguagem Pura). Você agora possui o conhecimento necessário para entender 95% de qualquer código Python profissional.

Os próximos passos no Roadmap envolveriam frameworks específicos (como Django para Web, Pandas para Ciência de Dados ou PyTorch para IA), que já são considerados trilhas de especialização à parte do "Python propriamente dito".

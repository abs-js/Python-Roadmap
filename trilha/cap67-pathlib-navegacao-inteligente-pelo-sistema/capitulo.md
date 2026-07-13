# Capítulo 67: Pathlib – Navegação Inteligente pelo Sistema

### Teoria Sem Enrolação
Antigamente, para lidar com pastas e arquivos no Python, usávamos o módulo `os.path`. Ele tratava caminhos como simples textos (strings), o que gerava códigos confusos e cheios de barras invertidas. O **Pathlib** trouxe o conceito de **Caminhos como Objetos**.
- Com ele, um caminho não é só um texto, mas um objeto com "superpoderes": você pode verificar se é uma pasta, criar diretórios, ler o conteúdo de arquivos e até navegar usando o operador barra `/` de um jeito elegante, independente de estar no Windows, Linux ou Mac.

### A Grande Analogia
Imagine que o sistema de arquivos do seu computador é um **Labirinto de Caixas**.
O jeito antigo (`os.path`) era como você tentar explicar o caminho escrevendo um bilhete longo: "Vá para a sala A, depois no corredor B, entre na gaveta C". Se você errasse uma vírgula, o endereço quebrava.
O **Pathlib** é como ter um **Drone com GPS**. Você não dá instruções cegas; você diz ao drone: "Encontre o arquivo X". O drone entende onde está, sabe voar sobre obstáculos e, se você pedir para ele "subir um nível", ele entende a estrutura do labirinto sem você precisar descrever o mapa inteiro.

### Desafio de Aplicação CLI: "O Faxineiro de Arquivos"
Crie um script que:
1. Verifique se existe uma pasta chamada `Downloads_Temporarios` no diretório atual.
2. Se não existir, crie a pasta.
3. Crie 3 arquivos de texto vazios dentro dela (`temp1.txt`, `temp2.txt`, `temp3.txt`).
4. Liste todos os arquivos da pasta que terminam com `.txt`.

### Gabarito do Desafio
```python
from pathlib import Path

# Definindo o caminho da pasta como um objeto
pasta = Path("Downloads_Temporarios")

# 1 e 2. Verificando e criando a pasta
if not pasta.exists():
    pasta.mkdir()
    print(f"Pasta {pasta} criada!")

# 3. Criando arquivos usando o operador / para combinar caminhos
for i in range(1, 4):
    arquivo = pasta / f"temp{i}.txt"
    arquivo.touch() # Cria o arquivo vazio

# 4. Listando arquivos .txt na pasta
print("Arquivos encontrados:")
for txt in pasta.glob("*.txt"):
    print(f"- {txt.name}")
```

### Quiz de Fixação
1. Qual o operador que o Pathlib usa para juntar pastas e nomes de arquivos de forma elegante?
   > **Resposta:** O operador de divisão `/`.
2. Como verificamos se um caminho aponta para um diretório (pasta) real?
   > **Resposta:** Usando o método `.is_dir()`.
3. Qual a vantagem de usar Pathlib em vez de strings simples para caminhos?
   > **Resposta:** Portabilidade entre sistemas operacionais (ele ajusta as barras automaticamente) e acesso a métodos úteis integrados no objeto.

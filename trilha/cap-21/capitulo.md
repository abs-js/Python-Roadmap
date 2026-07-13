# Capítulo 21: Trabalhando com JSON e APIs – A Linguagem da Internet

### Teoria Sem Enrolação
- **JSON:** É o formato padrão para troca de dados na web. Ele se parece exatamente com um dicionário de Python.
- **Requisições HTTP:** São as "mensagens" que enviamos para servidores para pedir dados. 
- **Módulo `json`:** Converte strings JSON para dicionários Python (`json.loads`) e vice-versa (`json.dumps`).
- **Módulo `requests`:** (Biblioteca externa) Permite que seu código acesse sites e APIs de forma simples.

### A Grande Analogia
Imagine que você está em um **Restaurante de Delivery**.
Você (seu programa Python) é o cliente. A **API** é o cardápio e o sistema de pedidos do restaurante.
Você faz uma **Requisição** (o pedido). O restaurante processa e te envia uma **Marmita**.
O **JSON** é a marmita: ela tem divisórias organizadas para o arroz, o feijão e a carne. Quando a marmita chega na sua casa, você "abre" as divisórias (converte o JSON para Dicionário) e pode comer cada ingrediente separadamente.

### Desafio de Aplicação CLI: "Consultor de Endereços (CEP)"
Crie um programa que peça um CEP ao usuário e consulte a API pública `viacep.com.br`. O programa deve exibir o Logradouro, Bairro e Cidade. (Nota: Para este desafio, simule a resposta caso não tenha a lib `requests` instalada).

### Gabarito do Desafio
```python
import json
import requests # Lembre-se: pip install requests

cep = input("Digite o seu CEP (apenas números): ")
url = f"https://viacep.com.br/ws/{cep}/json/"

try:
    resposta = requests.get(url)
    # resposta.json() já converte o JSON da internet em um dicionário Python
    dados = resposta.json()

    if "erro" not in dados:
        print(f"--- ENDEREÇO ENCONTRADO ---")
        print(f"Rua: {dados['logradouro']}")
        print(f"Bairro: {dados['bairro']}")
        print(f"Cidade: {dados['localidade']}")
    else:
        print("CEP não encontrado.")

except Exception as e:
    print(f"Erro na conexão: {e}")
```

### Quiz de Fixação
1. Qual estrutura de dados do Python é a "irmã gêmea" do formato JSON?
   > **Resposta:** O Dicionário (`dict`).
2. Qual método da biblioteca `requests` usamos para buscar dados em uma URL?
   > **Resposta:** O método `.get()`.
3. Como transformamos um dicionário Python em uma string no formato JSON?
   > **Resposta:** Usando `json.dumps(seu_dicionario)`.

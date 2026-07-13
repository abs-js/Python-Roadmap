# Capítulo 33: Logging – O Diário de Bordo Profissional

### Teoria Sem Enrolação
Usar `print()` para entender o que está acontecendo no seu código é coisa de iniciante. Em sistemas reais, usamos o **Logging**. 
O logging permite registrar mensagens com diferentes níveis de importância:
- **DEBUG:** Detalhes técnicos para desenvolvedores.
- **INFO:** Confirmação de que as coisas estão funcionando.
- **WARNING:** Algo inesperado aconteceu (um aviso).
- **ERROR:** Um problema sério impediu uma função de rodar.
- **CRITICAL:** O programa inteiro pode parar.
A grande vantagem é que você pode salvar esses registros em um arquivo `.log` para analisar depois.

### A Grande Analogia
Imagine a **Caixa Preta de um Avião**. 
Enquanto o voo está normal, ela vai registrando: "Altitude OK", "Combustível OK" (nível INFO). Se uma turbulência acontece, ela registra: "Vento Forte" (WARNING). Se um motor falha, ela registra: "Motor 1 Parou" (CRITICAL). 
O piloto não precisa ficar lendo isso o tempo todo, mas se o avião cair (o programa der crash), os engenheiros pegam a caixa preta (o arquivo de log) e descobrem exatamente o que aconteceu e em qual segundo aconteceu.

### Desafio de Aplicação CLI: "Sistema de Monitoramento de Servidor"
Crie um script que configure o logging para salvar mensagens em um arquivo chamado `sistema.log`.
1. Registre uma mensagem de INFO dizendo "Servidor iniciado".
2. Simule um erro de conexão e registre uma mensagem de ERROR dizendo "Falha ao conectar ao Banco de Dados".
3. Verifique se o arquivo foi criado e contém as mensagens.

### Gabarito do Desafio
```python
import logging

# Configurando o logger: nome do arquivo, nível mínimo e formato da mensagem
logging.basicConfig(
    filename='sistema.log',
    level=logging.DEBUG,
    format='%(asctime)s - %(levelname)s - %(message)s'
)

logging.info("O servidor foi iniciado com sucesso.")

try:
    # Simulando um erro proposital
    resultado = 10 / 0
except ZeroDivisionError:
    logging.error("Tentativa de divisão por zero detectada no processamento!")

logging.warning("O uso de memória está acima de 80%.")
print("Logs registrados no arquivo sistema.log!")
```

### Quiz de Fixação
1. Qual o nível de log usado para avisar sobre algo que não é um erro agora, mas pode ser um problema no futuro?  
   > **Resposta:** WARNING.
2. Qual a principal vantagem do logging sobre o `print()`?  
   > **Resposta:** A capacidade de categorizar mensagens por níveis, formatar timestamps automaticamente e redirecionar a saída para arquivos de forma organizada.
3. Se eu configurar o nível para `INFO`, as mensagens de `DEBUG` aparecerão no log?  
   > **Resposta:** Não, apenas mensagens de nível `INFO` e superiores (Warning, Error, Critical) aparecerão.

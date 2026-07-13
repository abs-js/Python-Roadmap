# Capítulo 74: Subprocess – O Maestro do Sistema Operacional

### Teoria Sem Enrolação
Às vezes, o Python não tem uma biblioteca nativa para algo, mas o seu computador tem um programa de linha de comando que faz. O módulo **`subprocess`** permite que o Python "digite" comandos no terminal para você.
- **`run()`**: Executa um comando e espera ele terminar.
- **`check_output()`**: Executa um comando e captura o que ele escreveu na tela.
- É a ferramenta definitiva para automação de TI, permitindo que o Python controle outros softwares.

### A Grande Analogia
Imagine que o Python é um **Executivo de uma Empresa**.
Ele é muito inteligente, mas não sabe operar a máquina de xerox ou limpar as janelas. Para isso, ele chama um **Terceirizado (Subprocess)**. O executivo entrega um bilhete com a ordem ("Limpe a janela"), o terceirizado sai da sala, faz o trabalho no corredor (o sistema operacional) e volta com o relatório do que foi feito. O executivo não precisou sujar as mãos; ele apenas gerenciou quem sabia fazer.

### Desafio de Aplicação CLI: "O Inspetor de Rede"
Crie um script que use o comando `ping` do sistema operacional para verificar se o site `google.com` está acessível. O Python deve disparar o comando e informar ao usuário se a conexão está ativa ou não com base no resultado do comando.

### Gabarito do Desafio
```python
import subprocess
import platform

def verificar_conexao(site):
    # O comando muda levemente entre Windows e Linux/Mac
    parametro = "-n" if platform.system().lower() == "windows" else "-c"
    comando = ["ping", parametro, "1", site]
    
    print(f"Verificando {site}...")
    
    # Executa o comando e captura o status de retorno (0 = Sucesso)
    resultado = subprocess.run(comando, stdout=subprocess.PIPE, stderr=subprocess.PIPE)
    
    if resultado.returncode == 0:
        print("Sucesso: O servidor respondeu!")
    else:
        print("Erro: Não foi possível alcançar o servidor.")

verificar_conexao("google.com")
```

### Quiz de Fixação
1. Qual função do `subprocess` é recomendada para a maioria das tarefas de execução?
   > **Resposta:** `subprocess.run()`.
2. O que o valor `0` no `returncode` costuma significar nos sistemas operacionais?
   > **Resposta:** Sucesso (o comando terminou sem erros).
3. Por que passamos os comandos como uma lista `["ping", "google.com"]` em vez de uma string única?
   > **Resposta:** Por segurança (evita injeção de comandos de shell) e para que o Python trate cada argumento corretamente.

# Capítulo 71: Shutil – O Gerente de Mudanças e Logística

### Teoria Sem Enrolação
O módulo `pathlib` é ótimo para navegar, mas quando o assunto é "trabalho pesado" com arquivos e pastas, o **`shutil`** (Shell Utilities) é o especialista. 
- Ele permite copiar arquivos (`copy`), mover pastas inteiras (`move`), deletar árvores de diretórios (`rmtree`) e até criar arquivos compactados (.zip ou .tar) com um único comando. 
- Diferente do `os.remove()`, que só apaga arquivos, o `shutil` lida com a estrutura completa de forma recursiva.

### A Grande Analogia
Imagine que o `pathlib` é o seu **GPS**: ele te diz onde as coisas estão. Já o `shutil` é o **Caminhão de Mudança** com uma equipe de carregadores.
Se você precisa levar uma caixa (arquivo) de um bairro para outro, o caminhão faz isso. Se você precisa demolir um prédio inteiro e limpar o terreno (deletar pasta com arquivos dentro), a equipe do `shutil` traz as escavadeiras. Ele não se preocupa apenas com o endereço, mas com o transporte físico e o empacotamento da carga.

### Desafio de Aplicação CLI: "O Compactador de Backups"
Crie um script que:
1. Crie uma pasta chamada `Meus_Documentos`.
2. Salve um arquivo `notas.txt` lá dentro.
3. Use o `shutil` para criar um arquivo comprimido (`.zip`) de toda a pasta `Meus_Documentos`.
4. Mova esse arquivo `.zip` para uma nova pasta chamada `Backup_Final`.

### Gabarito do Desafio
```python
import shutil
import os
from pathlib import Path

# Preparando o terreno
Path("Meus_Documentos").mkdir(exist_ok=True)
with open("Meus_Documentos/notas.txt", "w") as f:
    f.write("Dados ultra secretos de Python.")

# 1. Compactando a pasta em um arquivo .zip
# 'backup_projeto' é o nome do arquivo, 'zip' o formato, '.' o diretório base
shutil.make_archive("backup_projeto", "zip", "Meus_Documentos")
print("Arquivo ZIP criado!")

# 2. Criando pasta de destino e movendo
Path("Backup_Final").mkdir(exist_ok=True)
shutil.move("backup_projeto.zip", "Backup_Final/backup_projeto.zip")
print("Backup movido para a pasta final!")
```

### Quiz de Fixação
1. Qual função do `shutil` usamos para deletar uma pasta que não está vazia?
   > **Resposta:** `shutil.rmtree()`.
2. Qual a diferença entre `shutil.copy()` e `shutil.copy2()`?
   > **Resposta:** O `copy2()` tenta preservar também os metadados do arquivo (como data de criação e modificação).
3. Posso usar o `shutil.move()` para renomear um arquivo?
   > **Resposta:** Sim, mover um arquivo para o mesmo diretório com um nome diferente é a forma padrão de renomear em nível de sistema.

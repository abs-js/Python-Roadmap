# Capítulo 38: Shallow vs Deep Copy — O Espelho da Memória

### Teoria Sem Enrolação
Em Python, quando você faz `lista_b = lista_a`, você não criou uma lista nova; você apenas deu dois nomes para o mesmo objeto na memória. Você "Conectou" eles: Se mudar a `lista_b`, a `lista_a` também muda. Para evitar isso, usamos cópias:
- **Shallow Copy (Cópia Rasa):** Cria um novo objeto, mas se houver listas dentro de listas, os itens internos ainda são referências aos originais.
- **Deep Copy (Cópia Profunda):** Cria um novo objeto e percorre todas as sublistas criando cópias de tudo. É uma independência total.

### A Grande Analogia
Imagine que você tem uma **Pasta de Arquivos Física** com documentos originais.
- **Referência (`=`):** É dar a chave da sua gaveta para um amigo. Se ele rasgar um papel, você perdeu o original.
- **Shallow Copy:** É tirar uma xerox da pasta. Agora você tem uma pasta nova, mas se dentro dela houver um **Cartão de Visitas** original preso com um clipe, e seu amigo mudar o telefone no cartão, o seu cartão (que é o mesmo) também mudou.
- **Deep Copy:** É contratar um artista para recriar cada papel, cada item e cada detalhe em uma sala nova. Nada do que acontecer na sala dele afetará a sua.

### Pequena analogia:
Você criou uma corrente entre as duas, se mudar um muda outro. Ponto final.

### Desafio de Aplicação CLI: "O Simulador de Backup de Matriz"
Crie uma lista aninhada (matriz): `labirinto = [['X', ' '], [' ', ' ']]`.
1. Faça uma cópia rasa e tente mudar o primeiro elemento.
2. Faça uma cópia profunda (usando o módulo `copy`) e mude o primeiro elemento.
3. Imprima o original para ver em qual dos casos ele foi alterado indesejadamente.

### Gabarito do Desafio
```python
import copy

original = [['X', ' '], [' ', ' ']]

# Cópia Rasa (Shallow)
rasa = list(original)
rasa[0][0] = 'O' # Isso vai alterar o original!

print(f"Original após Shallow: {original}")

# Restaurando e fazendo Cópia Profunda (Deep)
original = [['X', ' '], [' ', ' ']]
profunda = copy.deepcopy(original)
profunda[0][0] = 'O' # Isso NÃO afeta o original

print(f"Original após Deep: {original}")
print(f"Cópia Profunda: {profunda}")
```

### Quiz de Fixação
1. Qual módulo do Python fornece as funções de cópia rasa e profunda?
   > **Resposta:** O módulo `copy`.
2. Se eu usar `lista.copy()`, estou fazendo uma cópia rasa ou profunda?
   > **Resposta:** Rasa (Shallow).
3. Por que a cópia profunda consome mais recursos do computador?
   > **Resposta:** Porque o Python precisa percorrer recursivamente toda a estrutura de dados e duplicar cada elemento individualmente na memória.

# Capítulo 69: Enum – A Lista de Opções Inabalável

### Teoria Sem Enrolação
Muitas vezes em programação usamos "números mágicos" ou strings soltas para representar opções (ex: 1 para "Ativo", 0 para "Inativo"). Isso causa erros de digitação e dificulta a leitura.
O **Enum** (Enumeration) permite criar um grupo de nomes simbólicos vinculados a valores constantes.
- Melhora a legibilidade.
- Evita que você use valores que não existem (tipo um estado "2" quando só deveria haver 0 ou 1).

### A Grande Analogia
Imagine que você está em um **Elevador Profissional**.
Você não aperta qualquer botão ou desenha um número no painel. O painel tem **Botões Fixos**: Térreo, 1º Andar, 2º Andar e Cobertura. O **Enum** são esses botões. Você não consegue inventar o "Andar 99" se o botão não estiver lá. Ter um Enum garante que todos no seu código falem a mesma língua e usem apenas as opções permitidas pelo painel.

### Desafio de Aplicação CLI: "O Status do Guerreiro"
1. Crie um Enum chamado `Estado` com as opções: `SAUDAVEL`, `FERIDO` e `CRITICO`.
2. Crie uma função que receba um desses estados.
3. Se o estado for `CRITICO`, a função deve retornar "CHAME UM MÉDICO!". Caso contrário, "Continue lutando!".

### Gabarito do Desafio
```python
from enum import Enum, auto

class Estado(Enum):
    SAUDAVEL = auto() # auto() atribui um número automático (1, 2, 3...)
    FERIDO = auto()
    CRITICO = auto()

def verificar_situacao(status):
    if status == Estado.CRITICO:
        return "ALERTA: CHAME UM MÉDICO!"
    return "Tudo sob controle. Continue lutando!"

# Testando
meu_status = Estado.CRITICO
print(f"Status atual: {meu_status.name}") # .name exibe o nome do item
print(verificar_situacao(meu_status))
```

### Quiz de Fixação
1. Qual o benefício de usar `auto()` em um Enum?
   > **Resposta:** Ele atribui valores numéricos automaticamente, removendo a necessidade de você mesmo gerenciar os números (1, 2, 3...).
2. Como acessamos o "nome" legível de um membro do Enum (ex: 'SAUDAVEL')?
   > **Resposta:** Através da propriedade `.name`.
3. É possível ter dois nomes diferentes com o mesmo valor dentro de um Enum?
   > **Resposta:** Por padrão sim (o segundo vira um apelido), mas se quiser proibir isso, deve-se usar o decorador `@unique`.

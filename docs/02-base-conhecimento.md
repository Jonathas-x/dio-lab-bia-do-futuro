# Base de Conhecimento

## Dados Utilizados

| Arquivo | Formato | Para quer serve no Fait |
|---------|---------|---------------------|
| `historico_atendimento.csv` | CSV | Contextualizar interações anteriores ou seja, dar continuidade ao atendimento de forma mais eficiente.|
| `perfil_investidor.json` | JSON | Personalizar explicações sobre as dúvidas e necessidades de aprendizado do cliente. |
| `produtos_financeiros.json` | JSON | Conhecer os produtos disponíveis para que eles possam ser ensinados ao cliente. |
| `transacoes.csv` | CSV | Analisar padrão de gastos do cliente e usar essas informações de forma didática. |

---

## Adaptações nos Dados

> Você modificou ou expandiu os dados mockados? Descreva aqui.

Perfil de risco do cliente

Histórico de transações com data, categoria e valor

Metadados auxiliares (ex.: limite mensal, objetivos financeiros)

---

## Estratégia de Integração

### Como os dados são carregados?
``` python

import json
import pandas as pd

# ===== CARREGAR DADOS ====== #
perfil = json.load(open('./data/perfil_investidor.json'))
transacoes = pd.read_csv(open('./data/transacoes.csv'))
historico = pd.read_csv(open('./data/historico_atendimento.csv'))
produto = json.load(open('./data/produtos_financeiros.json'))

```

### Como os dados são usados no prompt?
> Os dados vão no system prompt? São consultados dinamicamente?

Inseridas dinamicamente a cada pergunta relevante, ou

Recuperadas sob demanda via função/tooling (quando aplicável)

---

## Exemplo de Contexto Montado

> Mostre um exemplo de como os dados são formatados para o agente.

```
Dados do Cliente:
- Nome: João Silva
- Perfil: Moderado
- Saldo disponível: R$ 5.000

Últimas transações:
- 01/11: Supermercado - R$ 450
- 03/11: Streaming - R$ 55
...
```

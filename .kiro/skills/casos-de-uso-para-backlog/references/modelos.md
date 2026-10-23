# Modelos de Epic, Feature e PBI

Use exatamente esta estrutura no chat e no arquivo `docs/backlog/<epic>.md`.

## Arquivo de backlog (um por epic)

```markdown
# E-01 · Cobrança na saída
**Objetivo de negócio:** cobrar o valor correto e liberar a saída sem operador.
**Casos de uso:** UC-01
**Board:** #4810

## F-02 · Limites de cobrança
**Trecho do fluxo:** UC-01, passo 4
**Valor demonstrável:** permanências longas nunca pagam acima da tabela.
**Board:** #4811

### PBI-05 · Limitar a cobrança ao teto diário
(modelo de PBI abaixo)
```

## Modelo de PBI

```markdown
### PBI-05 · Limitar a cobrança ao teto diário
**Board:** #4821 · **Rastreio:** UC-01 passo 4 · RN-03

**História**
Como cliente, quero pagar no máximo o valor da diária,
para não ser cobrado acima da tabela quando fico muitas horas.

**Critérios de aceite**
Fronteira de RN-03: R$ 40,00 é **permitido** (inclusivo); nenhum valor calculado acima
disso é cobrado dentro do mesmo período de 24 horas.

- Cenário 1 · exatamente no teto
  - Dado um cálculo de R$ 40,00 para a permanência
  - Quando o cliente paga
  - Então o valor cobrado é R$ 40,00
- Cenário 2 · acima do teto
  - Dado um cálculo de R$ 48,00 para a permanência, dentro de 24 horas
  - Quando o cliente paga
  - Então o valor cobrado é R$ 40,00

**INVEST**
| I | N | V | E | S | T |
|---|---|---|---|---|---|
| ✓ não depende de outro PBI | ✓ não define a tela | ✓ evita cobrança indevida | ✓ regra conhecida | ✓ 2 cenários | ✓ fronteira numérica |

**Perguntas em aberto**
- Como cobrar a permanência acima de 24 horas? (UC-01 não detalha)
```

Regras do modelo:
- IDs locais (`E-01`, `F-01`, `PBI-01`) são sequenciais no projeto; o ID do board entra
  na linha **Board** depois da publicação.
- A linha "Fronteira" é obrigatória sempre que houver número ou limite na regra.
- Sem perguntas em aberto, omita a seção.

## Mapeamento para o board

### Azure DevOps

| Backlog | Processo Scrum | Processo Agile | Campo |
|---|---|---|---|
| Epic | Epic | Epic | Título, Descrição (objetivo + UCs) |
| Feature | Feature | Feature | Pai = Epic |
| PBI | Product Backlog Item | User Story | Pai = Feature |
| História | Description | Description | |
| Critérios de aceite | Acceptance Criteria | Acceptance Criteria | `Microsoft.VSTS.Common.AcceptanceCriteria` |
| Rastreio | Tags | Tags | `UC-01; RN-03` |

Crie o item e depois o link de hierarquia (pai/filho). Confirme o tipo de processo antes
da primeira publicação.

### Jira

| Backlog | Tipo de item | Observação |
|---|---|---|
| Epic | Epic | |
| Feature | Feature, se o projeto tiver esse tipo; senão Story com label `feature` | Pai = Epic |
| PBI | Story | Pai = Feature (ou Epic, se não houver nível de feature) |
| Critérios de aceite | campo de critérios do projeto ou seção na descrição | |
| Rastreio | Labels | `UC-01`, `RN-03` |

# Estacionamento · cobrança e saída

Sistema de cobrança para um estacionamento rotativo. O cliente retira um ticket na
entrada e, na saída, paga no totem o tempo que o carro ficou estacionado. O sistema
calcula o valor pelas regras de tarifa, registra o pagamento e libera a cancela.

## Objetivos

- Cobrar sempre o valor correto, de acordo com a tabela de tarifas.
- Reduzir filas na saída com pagamento no totem, sem operador.
- Dar ao gerente uma visão confiável do faturamento.

## Requisitos funcionais

| ID | Requisito | Caso de uso | Status |
|---|---|---|---|
| RF-01 | O sistema calcula a permanência a partir da data e hora de entrada do ticket | UC-01 | Em refinamento |
| RF-02 | O sistema calcula o valor a pagar pela tabela de tarifas (tolerância, hora ou fração, teto) | UC-01 | Em refinamento |
| RF-03 | O cliente vê a permanência e o valor antes de pagar | UC-01 | Em refinamento |
| RF-04 | O cliente paga no totem e a saída é liberada | UC-01 | Em refinamento |
| RF-05 | O cliente que perdeu o ticket paga um valor fixo e sai | UC-01 | Em refinamento |
| RF-06 | O sistema emite o ticket na entrada com data e hora | UC-02 | Futuro |
| RF-07 | Mensalistas entram e saem sem pagar por permanência | UC-03 | Futuro |
| RF-08 | O cliente paga antecipadamente pelo app e sai sem passar no totem | UC-04 | Futuro |
| RF-09 | O painel da entrada mostra as vagas livres | UC-05 | Futuro |
| RF-10 | O gerente consulta o faturamento por dia e por forma de pagamento | UC-06 | Futuro |

O escopo atual é o **UC-01 · Pagar o estacionamento na saída** (RF-01 a RF-05). Os demais
casos de uso ainda não foram escritos.

## Tabela de tarifas

| Permanência | Valor |
|---|---|
| Até 15 minutos | Grátis |
| Depois da tolerância | R$ 8,00 por hora ou fração |
| Teto | R$ 40,00 a cada 24 horas |
| Ticket perdido | R$ 50,00 |

As regras completas estão em `docs/casos-de-uso/UC-01-pagar-estacionamento.md`.

## Requisitos não funcionais

| ID | Requisito |
|---|---|
| RNF-01 | **Exatidão**: valores monetários em decimal com duas casas, nunca em ponto flutuante |
| RNF-02 | **Desempenho**: o valor aparece no totem em menos de 2 segundos após a leitura do ticket |
| RNF-03 | **Auditoria**: todo pagamento guarda entrada, saída, permanência, valor e regra aplicada |
| RNF-04 | **Disponibilidade**: sem conexão com o servidor, o totem calcula e registra localmente e sincroniza depois |
| RNF-05 | **Testabilidade**: toda regra de tarifa tem testes automatizados ligados ao PBI de origem |

## Documentação

```
docs/
├── casos-de-uso/          casos de uso (UC-xx), fonte dos requisitos e das regras de negócio
├── backlog/               epics, features e PBIs aprovados, com rastreio até o caso de uso
└── testes-validados.md    testes aprovados por uma pessoa; são o contrato das regras
```

## Fluxo de desenvolvimento

1. **Backlog**: os casos de uso viram Epic → Feature → PBI pela skill
   `casos-de-uso-para-backlog`, com aprovação a cada nível.
2. **Steering**: o agente `start` registra stack, estrutura e domínio em `.kiro/steering/`.
3. **Testes**: o agente `tdd` transforma os critérios de aceite de uma feature em testes,
   que só viram contrato depois de validados por uma pessoa.
4. **Código**: implementado pela IA ou por uma pessoa, sempre contra os testes validados.

A stack ainda não foi definida; ela é registrada em `.kiro/steering/tech.md`.

# UC-01 · Pagar o estacionamento na saída

**Ator principal:** Cliente (motorista)
**Objetivo:** pagar o tempo em que o carro ficou no estacionamento e sair.
**Pré-condição:** o cliente tem o ticket emitido na entrada, com data e hora de entrada
(horas e minutos).
**Pós-condição:** pagamento registrado e saída liberada.

## Fluxo principal

1. Cliente insere o ticket no totem de pagamento.
2. Sistema lê a data e a hora de entrada do ticket.
3. Sistema calcula a permanência até o momento atual.
4. Sistema calcula o valor a pagar conforme as regras de cobrança.
5. Sistema exibe a permanência e o valor.
6. Cliente paga.
7. Sistema registra o pagamento e libera a saída.

## Fluxos alternativos

- **1a. Ticket perdido**: cliente informa que perdeu o ticket; sistema cobra o valor de
  ticket perdido (RN-04) e segue no passo 6.
- **4a. Permanência dentro da tolerância**: valor é zero; sistema libera a saída sem
  pagamento.
- **6a. Cliente desiste**: sistema devolve o ticket e nada é registrado.

## Regras de negócio

- **RN-01 · Tolerância**: permanência de até 15 minutos é gratuita.
- **RN-02 · Hora ou fração**: passada a tolerância, cobra-se R$ 8,00 por hora ou fração,
  contadas desde a entrada.
- **RN-03 · Teto**: o valor não passa de R$ 40,00 a cada 24 horas de permanência.
- **RN-04 · Ticket perdido**: valor fixo de R$ 50,00, no lugar do cálculo por permanência.

## Fora do escopo

Emissão do ticket na entrada, mensalistas, pagamento antecipado pelo app e controle de
vagas. Cada um é outro caso de uso.

## Glossário

- **Permanência**: tempo entre a entrada registrada no ticket e o momento do pagamento.
- **Tolerância**: tempo inicial em que não há cobrança.
- **Fração**: parte de uma hora que ainda não se completou.
- **Teto**: valor máximo cobrado por período de 24 horas.

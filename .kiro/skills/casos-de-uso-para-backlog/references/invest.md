# INVEST: como checar e como quebrar

## As seis perguntas

| Letra | Pergunta | Reprova quando |
|---|---|---|
| **I** Independente | Dá para entregar sem esperar outro PBI? | Só faz sentido junto com outro card; ordem rígida entre os dois |
| **N** Negociável | Descreve o problema, sem travar a solução? | Diz "usar tabela X", "criar endpoint Y", "botão azul" |
| **V** Valioso | Alguém (usuário, PO, negócio) percebe valor quando fica pronto? | É tarefa técnica pura ("criar entidade Ticket") |
| **E** Estimável | O time consegue dimensionar? | Tem regra desconhecida ou dependência externa não resolvida |
| **S** Pequeno (*Small*) | Cabe em poucos dias de trabalho? | Mais de 4 ou 5 cenários de aceite, ou cobre vários fluxos |
| **T** Testável | Existe critério objetivo de pronto? | Usa "rápido", "fácil", "melhorar", "adequado" sem número |

O **T** é a ponte com o resto do fluxo: se não dá para testar, o agente TDD não tem o
que fazer.

## Exemplos

- ✗ "Melhorar a cobrança do estacionamento": não é pequeno, não é estimável, não é testável.
- ✓ "Limitar a cobrança a R$ 40,00 por período de 24 horas": pequeno, independente,
  com fronteira clara.

## Tarefa técnica não é PBI

"Criar tabela de tarifas" não entrega valor sozinha. Ela é uma *task* dentro do PBI
que precisa dela. Se aparecer como PBI, funda no comportamento que a justifica.

## Como quebrar (SPIDR)

Quando um PBI reprova no **S** ou no **E**, use um destes cortes, nesta ordem de
preferência:

1. **Paths (caminhos)**: um PBI por fluxo. O fluxo principal é um; cada fluxo
   alternativo do caso de uso (3a, 3b...) é outro.
2. **Rules (regras)**: um PBI por regra de negócio. "Calcular tarifa" vira
   "cobrar ticket perdido" (RN-04) e "aplicar o teto" (RN-03).
3. **Data (dados)**: comece com um tipo de dado e amplie (ex.: só carros de passeio,
   depois motos e utilitários).
4. **Interfaces**: uma interface por vez (ex.: totem primeiro, depois app do celular).
5. **Spike**: se o problema é desconhecimento técnico, crie um spike com prazo curto
   e pergunta clara; o PBI de verdade vem depois.

Nunca quebre por camada técnica ("PBI do banco", "PBI da tela"): cada pedaço precisa
continuar entregando valor de ponta a ponta.

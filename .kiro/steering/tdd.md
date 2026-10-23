---
inclusion: always
---

# Regras de TDD do projeto

Estas regras valem para qualquer agente que escreva testes ou código neste projeto.

## Regras

1. Nunca escreva código de produção antes de existir um teste falhando que o exija.
2. Todo critério de aceite vira pelo menos um teste.
3. Nomeie o teste pela **regra**, não pela função ("limita a cobrança ao teto diário",
   e não "calcular 2"), seguindo a convenção do framework de teste da stack.
4. Cubra as fronteiras: limite, limite + 1 e vazio. Diga se o limite é inclusivo ou exclusivo.
5. **Nunca altere um teste validado para fazer o código passar.** Se um teste validado
   parecer errado, pare e pergunte. Quem muda o contrato é gente.
6. Depois do Red, pergunte quem implementa (você ou a pessoa).

## Estrutura de um teste

- Comentário na primeira linha com o rastreio: `PBI-xx · RN-xx`.
- Corpo em três blocos, com comentários Dado, Quando e Então na sintaxe de comentário
  da linguagem do projeto.
- Um comportamento por teste. Dados mínimos, só os que a regra precisa.
- Verifique comportamento de negócio, não detalhe de implementação.

## Testes validados

Os testes aprovados por uma pessoa ficam listados em `docs/testes-validados.md`
(teste, PBI, regra, data, quem validou). Estar nessa lista significa: é contrato.

## Stack de testes

<!-- Preenchido pelo agente Start -->
- Framework: _a definir_
- Comando: _a definir_
- Pasta dos testes: _a definir_
- Padrão de nome dos arquivos: _a definir_

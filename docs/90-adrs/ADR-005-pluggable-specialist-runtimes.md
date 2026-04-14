# ADR-005, runtimes de especialistas como camada pluggable

- Status: aceito
- Data: 2026-04-14

## Contexto
A pesquisa aponta valor real em especialistas, handoffs e runtimes agentic, mas também mostra o risco de transformar esse runtime no núcleo administrativo do sistema.

## Decisão
Os runtimes de especialistas serão tratados como **camada pluggable e subordinada**, com interfaces estáveis e escopo delimitado.

## Racional
Especialistas devem executar trabalho cognitivo e ferramental dentro de contratos claros, sem se tornarem fonte canônica de estado, política, approval ou trilha global de auditoria.

## Consequências
### Positivas
- Facilita substituição de frameworks e fornecedores.
- Incentiva especialistas menores, mais claros e mais governáveis.
- Reduz acoplamento entre evolução do produto e evolução de um runtime específico.

### Tradeoffs
- Limita a tentação de concentrar inteligência e memória demais na camada agentic.
- Exige interfaces mais explícitas entre contrato, contexto, execução e saída.

## Implicações para a próxima fase
- Cada especialista futuro deve operar como unidade substituível, observável e delimitada.
- O control plane deve decidir quando e como um runtime é invocado.
- Memória, policy e estado durável não devem ficar dependentes de convenções internas de um runtime específico.

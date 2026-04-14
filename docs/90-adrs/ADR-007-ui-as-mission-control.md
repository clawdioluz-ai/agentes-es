# ADR-007, UI como mission control e não apenas chat

- Status: aceito
- Data: 2026-04-14

## Contexto
A pesquisa conclui que uma interface centrada só em chat é insuficiente para supervisionar trabalho multietapa, riscos, artefatos, approvals, evidências e exceções de forma legível para humanos.

## Decisão
A experiência de produto será orientada por uma **mission control UI**, e não por um paradigma chat-only.

Chat continuará útil, mas como superfície contextual subordinada ao estado da missão e aos objetos formais do sistema.

## Racional
O operador precisa enxergar missão, workflow, task, timeline, review queue, approvals, artefatos e observabilidade de forma integrada. Estado operacional deve ter precedência sobre narrativa conversacional.

## Consequências
### Positivas
- Torna o sistema mais legível, supervisionável e acionável.
- Melhora operação multiusuário e multi-missão.
- Favorece auditoria, priorização e intervenção humana explícita.
- Posiciona o produto como plataforma operacional, não apenas interface conversacional.

### Tradeoffs
- Aumenta a ambição de produto e UX.
- Exige modelo de navegação multi-nível e superfícies especializadas.
- Remove a simplicidade aparente de um produto centrado só em chat.

## Implicações para a próxima fase
- O design deve priorizar portfolio, mission detail, workflow board, timeline, review e approval surfaces.
- Eventos e comandos explícitos devem mediar mudanças de estado relevantes.
- Chat deve complementar entendimento e coordenação, não substituir o modelo operacional do sistema.

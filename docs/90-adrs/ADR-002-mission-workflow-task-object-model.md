# ADR-002, modelo de objetos mission, workflow e task

- Status: aceito
- Data: 2026-04-14

## Contexto
A pesquisa indica que tratar o sistema apenas como conversas com agentes empobrece o problema. A plataforma precisa de objetos de domínio explícitos para representar trabalho, progresso, handoffs, revisão, aprovação, artefatos e evidências.

## Decisão
A plataforma adotará um modelo de trabalho **mission-first**, com `mission`, `workflow` e `task` como objetos de primeira classe, acompanhados por objetos correlatos como `review`, `approval`, `handoff`, `artifact`, `agent` e `evidence`.

## Racional
- `mission` representa a unidade de intenção, ownership, risco e resultado.
- `workflow` representa a lógica de coordenação e progressão do trabalho.
- `task` representa a unidade operacional delegável e observável.

Esse modelo permite conectar estratégia, execução, supervisão e avaliação num mesmo sistema legível.

## Consequências
### Positivas
- Dá estrutura semântica para estado, responsabilidade e governança.
- Facilita operação humana acima do engine.
- Melhora rastreabilidade de handoffs e artefatos.
- Evita que chat, prompt ou run efêmera virem a unidade primária do produto.

### Tradeoffs
- Exige linguagem de domínio mais explícita desde cedo.
- Impõe maior cuidado com fronteiras entre objetos e ciclos de vida.

## Implicações para a próxima fase
- Interfaces, observabilidade e governança devem ser desenhadas em torno desses objetos.
- Conversas e execuções de agentes devem ser tratadas como eventos ou interações subordinadas ao modelo de trabalho.
- O backlog conceitual e futuro desenho técnico devem preservar esse vocabulário como base comum entre produto e arquitetura.

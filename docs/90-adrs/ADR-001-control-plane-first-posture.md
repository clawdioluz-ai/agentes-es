# ADR-001, postura control-plane-first

- Status: aceito
- Data: 2026-04-14

## Contexto
A pesquisa do repositório converge para um ponto central: o diferencial estratégico da plataforma não está em um agente único mais capaz, mas na coordenação governada de fluxos, contexto, decisões, risco e supervisão humana ao longo do SDLC.

## Decisão
A plataforma será definida como **control-plane-first**.

O control plane passa a ser o centro administrativo e semântico do sistema, responsável por identidade do trabalho, estado, políticas, checkpoints, evidências, exceções, ownership e coordenação entre camadas.

## Consequências
### Positivas
- Preserva separação clara entre coordenação e execução cognitiva.
- Favorece governança, auditabilidade e operação corporativa.
- Evita que o runtime de agentes capture a arquitetura inteira.
- Cria base mais estável para múltiplas superfícies, múltiplos fluxos e evolução futura.

### Tradeoffs
- Exige mais disciplina de modelagem do que uma arquitetura centrada só em agentes.
- Torna explícita uma camada de plataforma que não pode ser tratada como detalhe.
- Pode parecer mais pesada no início, mas reduz fragilidade estrutural depois.

## Implicações para a próxima fase
- Toda decisão técnica deve preservar o control plane como sistema de registro do trabalho agentic.
- Workflow engines, runtimes, interfaces e integrações devem permanecer subordinados a essa camada.
- O sucesso da plataforma será medido pela qualidade da coordenação governada, não apenas pela qualidade isolada dos especialistas.

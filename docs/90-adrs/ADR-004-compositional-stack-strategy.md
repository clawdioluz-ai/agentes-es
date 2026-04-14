# ADR-004, estratégia de stack composicional

- Status: aceito
- Data: 2026-04-14

## Contexto
A análise do landscape mostra que nenhuma ferramenta isolada resolve, ao mesmo tempo, control plane, workflow durável, execução cognitiva, observabilidade, governança e integração com o SDLC sem comprometer flexibilidade ou clareza de fronteiras.

## Decisão
A plataforma seguirá uma estratégia **composicional**, com separação deliberada entre:
- control plane
- backbone de workflow durável
- runtime cognitivo de especialistas
- observabilidade e avaliação
- integrações e superfícies operacionais

## Racional
O objetivo não é maximizar pureza arquitetural abstrata, mas preservar capacidade de evolução sem reiniciar a plataforma a cada troca de framework ou fornecedor.

## Consequências
### Positivas
- Reduz lock-in conceitual e tecnológico.
- Permite trocar peças sem desmontar a semântica da plataforma.
- Reforça a ideia de que o diferencial está na orquestração governada.

### Tradeoffs
- A cola entre camadas vira responsabilidade importante do desenho.
- Requer contratos explícitos e mais disciplina de integração.
- Pode parecer menos rápida do que escolher um framework totalizante como centro.

## Implicações para a próxima fase
- Não construir do zero workflow engine, runtime genérico de agentes ou stack básica de observabilidade.
- Concentrar construção própria em contratos, governança, evidência, políticas, handoffs e integração semântica com o SDLC.
- Avaliar tecnologias futuras pela capacidade de encaixe nessa decomposição, e não pelo apelo isolado do framework.

# Modelo de domínio conceitual

## Objetivo
Explicitar os principais objetos de domínio que tornam a plataforma legível, governável e extensível.

## Objetos iniciais
- mission
- workflow
- task
- handoff
- review
- approval
- agent
- artifact
- evidence
- policy
- exception
- integration capability

## Relações a explorar
- mission contém workflows e outcomes
- workflow coordena tasks e checkpoints
- task produz artifacts e evidence
- handoff transfere responsabilidade e contexto
- review e approval governam mudanças críticas de estado
- policy limita autonomia e acesso

## Questões a aprofundar
- quais objetos são canônicos no control plane?
- o que pertence ao domínio da plataforma versus ao domínio do SDLC integrado?
- como evitar um modelo excessivamente genérico?

# Orquestração fim a fim

## Papel do orquestrador
O orquestrador é responsável por:
- interpretar objetivo e restrições
- decompor trabalho
- selecionar especialistas
- sequenciar ou paralelizar etapas
- validar pré-condições e pós-condições
- manter rastreabilidade
- convocar checkpoints humanos
- consolidar evidências e métricas

## Coordenação entre agentes especialistas
Cada especialista deve atuar sobre um escopo limitado, com contrato claro de entrada, saída e critérios de qualidade.

## Handoffs entre etapas do SDLC
Handoffs devem ser tratados como objetos de primeira classe.
Cada handoff deve explicitar:
- artefato de entrada
- transformação esperada
- artefato de saída
- critérios de aceite
- risco
- responsável humano quando aplicável

## Contratos entre agentes
Um contrato deve conter no mínimo:
- objetivo da etapa
- formato esperado dos insumos
- formato esperado dos outputs
- políticas aplicáveis
- critérios de validação
- limites de autonomia
- condições de escalonamento

## Checkpoints humanos
Supervisão humana tende a ser mandatória em:
- decisões arquiteturais relevantes
- mudanças com alto impacto de negócio
- segurança, privacidade e compliance
- aprovação de release
- incidentes severos
- conflitos entre agentes ou baixa confiança

## Governança decisória
O fluxo precisa registrar:
- quem decidiu
- com base em qual evidência
- em qual etapa
- sob quais políticas
- com qual grau de confiança

## Observabilidade e rastreabilidade
A execução deve ser observável por:
- fluxo
- etapa
- agente
- artefato
- decisão
- tempo
- custo
- risco
- retrabalho

## Métricas sugeridas
- lead time por etapa
- taxa de retrabalho
- cobertura de artefatos obrigatórios
- taxa de escalonamento humano
- defeitos por mudança
- aderência a políticas
- confiança por decisão

## Gestão de risco
Risco deve ser avaliado por:
- criticidade da mudança
- sensibilidade dos dados
- impacto operacional
- confiança da evidência
- histórico de falhas similares

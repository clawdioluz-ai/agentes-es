# agentes-es

Pesquisa estratégica e arquitetural sobre orquestração fim a fim do desenvolvimento de software com apoio de IA generativa.

## Objetivo
Consolidar uma base de pesquisa estruturada para orientar o desenho futuro de um framework de agentes/skills capazes de cobrir o SDLC ponta a ponta, com ênfase em orquestração fim a fim.

## Escopo desta fase
Esta fase é de análise, estrutura conceitual, taxonomia, arquitetura, governança, artefatos e referências.

### Exclusões explícitas
- sem implementação
- sem código funcional de agentes
- sem protótipos técnicos
- sem automações executáveis

## Perguntas de pesquisa
1. Como grandes empresas estão usando IA generativa ao longo do SDLC?
2. Quais etapas têm maior maturidade de uso?
3. Quais padrões de governança aparecem com mais frequência?
4. Como separar agentes especialistas de um agente orquestrador?
5. Como organizar handoffs e dependências entre etapas?
6. Quais artefatos circulam entre agentes ao longo do processo?
7. Onde a supervisão humana é mandatória?
8. Como medir qualidade, produtividade, risco e confiabilidade?
9. Como desenhar uma arquitetura de orquestração fim a fim sem cair em acoplamento excessivo?
10. Como transformar esse conhecimento em um framework reutilizável?

## Estrutura
- `docs/00-foundations/` visão geral, escopo, método e resumo executivo final
- `docs/10-benchmarking/` análise de empresas, plataformas e operating models
- `docs/20-sdlc/` mapeamento ponta a ponta do SDLC assistido por IA
- `docs/30-framework/` proposta consolidada de framework
- `docs/40-orchestration/` orquestração fim a fim, control plane e panorama de platform building
- `docs/50-governance/` governança, segurança, qualidade e métricas
- `docs/60-roadmap/` roadmap, hipóteses e questões abertas
- `docs/70-references/` bibliografia comentada e lista curta de referências principais
- `docs/80-meta/` distinção entre fato, inferência, proposta, guia do repositório e histórico consolidado

## Foco analítico obrigatório
- orquestração fim a fim
- separação entre agentes especialistas e orquestrador
- handoffs e contratos
- checkpoints humanos
- governança, métricas e rastreabilidade
- base suficiente para futura fase de desenho e implementação

## Status
Repositório agora contém um pacote de pesquisa estruturado, source-backed e coerente sobre orquestração ponta a ponta do SDLC com IA generativa. O conteúdo desta fase permanece conceitual e analítico.

## Entregáveis finais mais importantes
- `docs/00-foundations/01-executive-summary.md`
- `docs/30-framework/01-consolidated-framework-proposal.md`
- `docs/40-orchestration/01-end-to-end-orchestration.md`
- `docs/40-orchestration/02-operating-models-and-control-plane.md`
- `docs/40-orchestration/03-platform-building-landscape.md`
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/05-platform-stack-decision.md`
- `docs/40-orchestration/06-platform-blueprint.md`
- `docs/70-references/02-main-references.md`
- `docs/80-meta/02-repository-guide-and-history.md`

## Ordem de leitura recomendada
1. resumo executivo
2. benchmarking e metodologia
3. SDLC, artefatos e handoffs
4. framework e orquestração
5. governança, medição, roadmap e referências

## Documentos reforçados nesta etapa
- `docs/10-benchmarking/01-enterprise-benchmarking.md`
- `docs/30-framework/01-consolidated-framework-proposal.md`
- `docs/40-orchestration/01-end-to-end-orchestration.md`
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/05-platform-stack-decision.md`
- `docs/40-orchestration/06-platform-blueprint.md`
- `docs/70-references/01-commented-bibliography.md`
- `docs/80-meta/01-evidence-model.md`

## Documentos adicionados ou aprofundados anteriormente
- `docs/10-benchmarking/03-source-backed-patterns.md`
- `docs/20-sdlc/02-artifacts-handoffs-and-control-points.md`
- `docs/40-orchestration/02-operating-models-and-control-plane.md`
- `docs/40-orchestration/03-platform-building-landscape.md`
- `docs/50-governance/02-measurement-benchmarking-and-evidence.md`

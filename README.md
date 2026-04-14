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
- [`docs/00-foundations/`](docs/00-foundations/) visão geral, escopo, método, resumo executivo final e guia de decisão
- [`docs/10-benchmarking/`](docs/10-benchmarking/) análise de empresas, plataformas e operating models
- [`docs/20-sdlc/`](docs/20-sdlc/) mapeamento ponta a ponta do SDLC assistido por IA
- [`docs/30-framework/`](docs/30-framework/) proposta consolidada de framework e modelo conceitual de gestão do trabalho
- [`docs/40-orchestration/`](docs/40-orchestration/) orquestração fim a fim, control plane, blueprint de plataforma e cockpit operacional
- [`docs/50-governance/`](docs/50-governance/) governança, segurança, qualidade e métricas
- [`docs/60-roadmap/`](docs/60-roadmap/) roadmap, hipóteses e questões abertas
- [`docs/70-references/`](docs/70-references/) bibliografia comentada e lista curta de referências principais
- [`docs/80-meta/`](docs/80-meta/) distinção entre fato, inferência, proposta, guia do repositório e histórico consolidado
- [`docs/90-adrs/`](docs/90-adrs/) registro curto das decisões arquiteturais e de produto mais estruturantes para a próxima fase
- [`docs/100-software-design/`](docs/100-software-design/) pacote inicial de artefatos de design para traduzir a pesquisa em documentação arquitetural da próxima fase


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
- [`docs/00-foundations/01-executive-summary.md`](docs/00-foundations/01-executive-summary.md)
- [`docs/00-foundations/03-decision-guide.md`](docs/00-foundations/03-decision-guide.md)
- [`docs/30-framework/01-consolidated-framework-proposal.md`](docs/30-framework/01-consolidated-framework-proposal.md)
- [`docs/30-framework/03-work-management-model.md`](docs/30-framework/03-work-management-model.md)
- [`docs/40-orchestration/01-end-to-end-orchestration.md`](docs/40-orchestration/01-end-to-end-orchestration.md)
- [`docs/40-orchestration/02-operating-models-and-control-plane.md`](docs/40-orchestration/02-operating-models-and-control-plane.md)
- [`docs/40-orchestration/03-platform-building-landscape.md`](docs/40-orchestration/03-platform-building-landscape.md)
- [`docs/40-orchestration/04-target-architecture-proposal.md`](docs/40-orchestration/04-target-architecture-proposal.md)
- [`docs/40-orchestration/05-platform-stack-decision.md`](docs/40-orchestration/05-platform-stack-decision.md)
- [`docs/40-orchestration/06-platform-blueprint.md`](docs/40-orchestration/06-platform-blueprint.md)
- [`docs/40-orchestration/07-mission-control-ui-and-cockpit.md`](docs/40-orchestration/07-mission-control-ui-and-cockpit.md)
- [`docs/40-orchestration/08-mission-control-product-experience.md`](docs/40-orchestration/08-mission-control-product-experience.md)
- [`docs/40-orchestration/09-orchestration-platform-conceptual-prd.md`](docs/40-orchestration/09-orchestration-platform-conceptual-prd.md)
- [`docs/70-references/02-main-references.md`](docs/70-references/02-main-references.md)
- [`docs/80-meta/02-repository-guide-and-history.md`](docs/80-meta/02-repository-guide-and-history.md)
- [`docs/90-adrs/ADR-001-control-plane-first-posture.md`](docs/90-adrs/ADR-001-control-plane-first-posture.md)
- [`docs/90-adrs/ADR-002-mission-workflow-task-object-model.md`](docs/90-adrs/ADR-002-mission-workflow-task-object-model.md)
- [`docs/90-adrs/ADR-003-human-in-the-loop-governance.md`](docs/90-adrs/ADR-003-human-in-the-loop-governance.md)
- [`docs/90-adrs/ADR-004-compositional-stack-strategy.md`](docs/90-adrs/ADR-004-compositional-stack-strategy.md)
- [`docs/90-adrs/ADR-005-pluggable-specialist-runtimes.md`](docs/90-adrs/ADR-005-pluggable-specialist-runtimes.md)
- [`docs/90-adrs/ADR-006-evidence-and-auditability-first-class.md`](docs/90-adrs/ADR-006-evidence-and-auditability-first-class.md)
- [`docs/90-adrs/ADR-007-ui-as-mission-control.md`](docs/90-adrs/ADR-007-ui-as-mission-control.md)
- [`docs/100-software-design/01-design-artifact-stack.md`](docs/100-software-design/01-design-artifact-stack.md)
- [`docs/100-software-design/03-views-and-viewpoints.md`](docs/100-software-design/03-views-and-viewpoints.md)
- [`docs/100-software-design/04-quality-attribute-scenarios.md`](docs/100-software-design/04-quality-attribute-scenarios.md)
- [`docs/100-software-design/05-conceptual-domain-model.md`](docs/100-software-design/05-conceptual-domain-model.md)
- [`docs/100-software-design/06-decision-backlog.md`](docs/100-software-design/06-decision-backlog.md)
- [`docs/100-software-design/07-c4-conceptual-architecture.md`](docs/100-software-design/07-c4-conceptual-architecture.md)

## Ordem de leitura recomendada
1. resumo executivo e guia de decisão
2. benchmarking e metodologia
3. SDLC, artefatos e handoffs
4. framework, gestão do trabalho e orquestração
5. governança, ADRs estratégicas, roadmap e referências

## Onde começar, dependendo da pergunta
- **Entender a tese central**: [`docs/00-foundations/01-executive-summary.md`](docs/00-foundations/01-executive-summary.md)
- **Tomar uma decisão arquitetural de alto nível**: [`docs/00-foundations/03-decision-guide.md`](docs/00-foundations/03-decision-guide.md)
- **Analisar evidência externa e padrões observados**: [`docs/10-benchmarking/03-source-backed-patterns.md`](docs/10-benchmarking/03-source-backed-patterns.md)
- **Entender o fluxo SDLC e os handoffs**: [`docs/20-sdlc/02-artifacts-handoffs-and-control-points.md`](docs/20-sdlc/02-artifacts-handoffs-and-control-points.md)
- **Ver a proposta consolidada de framework**: [`docs/30-framework/01-consolidated-framework-proposal.md`](docs/30-framework/01-consolidated-framework-proposal.md)
- **Ver a arquitetura-alvo e a direção de stack**: [`docs/40-orchestration/04-target-architecture-proposal.md`](docs/40-orchestration/04-target-architecture-proposal.md) e [`docs/40-orchestration/05-platform-stack-decision.md`](docs/40-orchestration/05-platform-stack-decision.md)
- **Entender a visão de produto e mission control**: [`docs/40-orchestration/08-mission-control-product-experience.md`](docs/40-orchestration/08-mission-control-product-experience.md) e [`docs/40-orchestration/09-orchestration-platform-conceptual-prd.md`](docs/40-orchestration/09-orchestration-platform-conceptual-prd.md)
- **Ver decisões estruturantes já cristalizadas**: [`docs/90-adrs/README.md`](docs/90-adrs/README.md)
- **Entender a lógica do pacote e seu histórico editorial**: [`docs/80-meta/02-repository-guide-and-history.md`](docs/80-meta/02-repository-guide-and-history.md)
- **Entrar na ponte entre pesquisa e design de software**: [`docs/100-software-design/README.md`](docs/100-software-design/README.md)

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
- `docs/00-foundations/` visão geral, escopo e método
- `docs/10-benchmarking/` análise de empresas, plataformas e operating models
- `docs/20-sdlc/` mapeamento ponta a ponta do SDLC assistido por IA
- `docs/30-framework/` proposta consolidada de framework
- `docs/40-orchestration/` orquestração fim a fim
- `docs/50-governance/` governança, segurança, qualidade e métricas
- `docs/60-roadmap/` roadmap, hipóteses e questões abertas
- `docs/70-references/` bibliografia comentada
- `docs/80-meta/` distinção entre fato, inferência, proposta e recomendação

## Foco analítico obrigatório
- orquestração fim a fim
- separação entre agentes especialistas e orquestrador
- handoffs e contratos
- checkpoints humanos
- governança, métricas e rastreabilidade
- base suficiente para futura fase de desenho e implementação

## Status
Repositório agora contém uma primeira base de pesquisa estruturada e source-backed sobre orquestração ponta a ponta do SDLC com IA generativa. O conteúdo desta fase permanece conceitual e analítico.

## Documentos adicionados nesta etapa
- `docs/10-benchmarking/03-source-backed-patterns.md`
- `docs/20-sdlc/02-artifacts-handoffs-and-control-points.md`
- `docs/40-orchestration/02-operating-models-and-control-plane.md`
- `docs/50-governance/02-measurement-benchmarking-and-evidence.md`

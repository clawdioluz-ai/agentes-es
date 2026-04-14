# Guia do repositório e histórico consolidado

## Objetivo
Oferecer uma visão curta e final de como ler este repositório como pacote de pesquisa coerente, além de registrar a evolução dos principais commits desta fase.

## Como o pacote se organiza

### 1. Fundamentos
- `docs/00-foundations/01-executive-summary.md` reúne a tese central, principais achados, recomendação principal e nível de confiança.
- `docs/00-foundations/02-research-methodology.md` explica recorte, método e critérios de qualidade.
- `docs/00-foundations/03-decision-guide.md` conecta o material do repositório em uma cadeia explícita de decisão, deixando claro o que já está sustentado, o que ainda é hipótese e quais escolhas devem ficar para a próxima fase.

### 2. Benchmarking e base factual
- `docs/10-benchmarking/01-enterprise-benchmarking.md` compara empresas, plataformas e sinais públicos de maturidade.
- `docs/10-benchmarking/02-frameworks-and-operating-models.md` organiza a tipologia comparativa dos modelos observados.
- `docs/10-benchmarking/03-source-backed-patterns.md` consolida padrões sustentados por fontes.

### 3. Mapa do problema ponta a ponta
- `docs/20-sdlc/01-end-to-end-sdlc-map.md` descreve o SDLC ampliado assistido por IA.
- `docs/20-sdlc/02-artifacts-handoffs-and-control-points.md` detalha artefatos, handoffs e checkpoints.

### 4. Síntese de framework e modelo operacional do trabalho
- `docs/30-framework/01-consolidated-framework-proposal.md` apresenta a proposta consolidada do framework.
- `docs/30-framework/02-agent-skill-taxonomy.md` organiza a taxonomia de especialistas e capacidades.
- `docs/30-framework/03-work-management-model.md` define a camada acima do orchestration engine, com operating model orientado a missão, objetos de domínio de primeira classe e ciclos de vida conceituais para mission e task.

### 5. Orquestração, control plane e cockpit operacional
- `docs/40-orchestration/01-end-to-end-orchestration.md` define a disciplina de coordenação fim a fim.
- `docs/40-orchestration/02-operating-models-and-control-plane.md` posiciona o control plane e suas camadas.
- `docs/40-orchestration/03-platform-building-landscape.md` compara blocos de mercado, frameworks e tradeoffs de composição.
- `docs/40-orchestration/04-target-architecture-proposal.md` propõe a arquitetura-alvo recomendada para uma plataforma de orquestração agentic orientada a software delivery.
- `docs/40-orchestration/05-platform-stack-decision.md` compara opções viáveis de stack e fecha com uma recomendação explícita de direção arquitetural.
- `docs/40-orchestration/06-platform-blueprint.md` transforma a pesquisa e a decisão de stack em uma north star unificada de produto e plataforma, deixando claro o que é obrigatório, o que é opcional, o que deve permanecer pluggable e em que sequência a plataforma deve evoluir.
- `docs/40-orchestration/07-mission-control-ui-and-cockpit.md` define a arquitetura conceitual da mission control UI, incluindo portfólio de missões, kanban, chat contextual, timeline, detail pane, review queue, approval surfaces, observability surfaces e a interação da interface com control plane e orchestration engine.
- `docs/40-orchestration/08-mission-control-product-experience.md` traduz a arquitetura do cockpit em uma visão de experiência de produto, com telas principais, jornadas, fluxos conceituais e wireframes textuais para mission inbox, portfolio, mission detail, chat contextual, review queue, approval center, observability e artifacts/evidence.
- `docs/40-orchestration/09-orchestration-platform-conceptual-prd.md` sintetiza a pesquisa e a arquitetura em formato de PRD conceitual, consolidando visão de produto, problema, usuários-alvo, jobs to be done, capacidades centrais, jornadas, modelo de objetos, não objetivos, restrições, métricas, lógica de rollout e riscos principais.

### 6. Governança, medição e roadmap
- `docs/50-governance/01-governance-security-quality-metrics.md` consolida controles, qualidade e risco.
- `docs/50-governance/02-measurement-benchmarking-and-evidence.md` propõe o modelo de avaliação.
- `docs/60-roadmap/01-maturity-roadmap.md` e `docs/60-roadmap/02-open-questions-and-hypotheses.md` traduzem a pesquisa em próximos passos e hipóteses.

### 7. Referências e disciplina intelectual
- `docs/70-references/01-commented-bibliography.md` contém a bibliografia comentada completa.
- `docs/70-references/02-main-references.md` contém a lista curta de referências principais.
- `docs/80-meta/01-evidence-model.md` explica a separação entre fato, inferência, proposta conceitual e recomendação futura.

### 8. ADRs estratégicas para a próxima fase
- `docs/90-adrs/README.md` organiza o conjunto inicial de ADRs.
- `docs/90-adrs/ADR-001-control-plane-first-posture.md` fixa a postura control-plane-first.
- `docs/90-adrs/ADR-002-mission-workflow-task-object-model.md` formaliza mission, workflow e task como objetos centrais.
- `docs/90-adrs/ADR-003-human-in-the-loop-governance.md` estabelece supervisão humana como primitive.
- `docs/90-adrs/ADR-004-compositional-stack-strategy.md` consolida a direção composicional da plataforma.
- `docs/90-adrs/ADR-005-pluggable-specialist-runtimes.md` mantém runtimes de especialistas como camada pluggable.
- `docs/90-adrs/ADR-006-evidence-and-auditability-first-class.md` torna evidência e auditabilidade preocupações centrais.
- `docs/90-adrs/ADR-007-ui-as-mission-control.md` posiciona a UI como cockpit operacional, não apenas chat.

## Leitura recomendada em cinco passos
1. Ler o resumo executivo e o guia de decisão.
2. Ler benchmarking, padrões source-backed e metodologia.
3. Ler SDLC, handoffs e pontos de controle.
4. Ler framework, modelo de gestão do trabalho e orquestração.
5. Fechar com governança, medição, roadmap e referências.

## Estrutura resumida do repositório

```text
README.md
/docs
  /00-foundations
  /10-benchmarking
  /20-sdlc
  /30-framework
  /40-orchestration
  /50-governance
  /60-roadmap
  /70-references
  /80-meta
  /90-adrs
```

## Histórico consolidado desta fase

1. **a4f33ec - docs: initialize research repository for end-to-end AI SDLC orchestration**  
   Estrutura inicial do pacote, pergunta de pesquisa, escopo, capítulos-base e primeira organização temática.

2. **a366680 - docs: add source-backed corpus on orchestration and evaluation**  
   Entrada de material mais forte sobre padrões sustentados por fonte, handoffs, control plane e medição.

3. **639030b - docs: update executive summary and curated references**  
   Reforço da narrativa central e curadoria de referências para sustentar melhor a tese do repositório.

4. **94b35d2 - Expand company benchmarking and bibliography**  
   Ampliação do benchmarking corporativo, cobertura de plataformas e bibliografia comentada.

5. **ec8b0a8 - Strengthen framework orchestration and evidence model**  
   Consolidação do framework, refinamento dos documentos de orquestração e explicitação do modelo de evidência.

6. **c6df77a - Add target architecture proposal for orchestration platform**  
   Inclusão de uma proposta de arquitetura-alvo centrada em control plane, workflow backbone, runtimes subordinados, memória governada, policy/approval fabric, observabilidade, extensibilidade e tradeoffs de build versus compose.

7. **90d5046 - Add stack decision brief for orchestration platform**  
   Inclusão de um documento decisório comparando opções de stack composicionais e mais centradas em frameworks de agentes, com recomendação final em favor de uma direção control-plane-first.

8. **Pending new commit - Add north star platform blueprint**  
   Inclusão de um blueprint final que conecta pesquisa, arquitetura-alvo e decisão de stack em uma visão north star de produto e plataforma, com componentes obrigatórios, componentes opcionais, princípios de desenho, blocos pluggable e sequência recomendada de evolução.

9. **Pending new commit - Add decision guide and strengthen roadmap narrative**  
   Inclusão de um guia explícito de decisão para ligar evidência, framework, arquitetura e roadmap em uma cadeia única de leitura, além de aprofundamento do roadmap de maturidade com capacidades, riscos dominantes e critérios de passagem entre níveis.

10. **Pending new commit - Add work management model and mission control layer**  
   Inclusão de uma continuação conceitual acima do orchestration engine, cobrindo operating model orientado a missão, objetos de domínio como mission, workflow, task, review, approval, handoff, artifact, agent e evidence, além da arquitetura do cockpit operacional e suas superfícies de supervisão humana.

11. **Pending new commit - Add product-facing mission control experience vision**  
   Inclusão de uma visão conceitual mais orientada a produto para a mission control, cobrindo telas principais, jornadas de uso, fluxos entre superfícies e wireframes conceituais para inbox, board, mission detail, chat contextual, review, approval, observability e navegação de artefatos e evidências.

12. **Pending new commit - Add conceptual PRD for orchestration platform product**  
   Inclusão de um PRD conceitual para a plataforma de orquestração, consolidando visão de produto, problema, segmentos de usuário, jobs to be done, proposta de valor, capacidades centrais, objeto de domínio, não objetivos, restrições, métricas, fases de rollout e riscos estratégicos.

13. **Pending new commit - Add initial strategic ADR set for the orchestration platform**  
   Inclusão de um conjunto inicial de ADRs conceituais para fixar as decisões mais estruturantes já implicadas pela pesquisa, cobrindo postura control-plane-first, modelo mission-workflow-task, governança human-in-the-loop, estratégia composicional de stack, runtimes especialistas pluggable, evidência e auditabilidade como preocupações de primeira classe e UI como mission control.

## Resultado final do pacote
### Inferência
O repositório agora se lê como uma pesquisa estratégica estruturada, com separação mais clara entre base factual, síntese analítica, proposta conceitual e recomendações futuras. Com a proposta de arquitetura-alvo, o documento decisório de stack, o platform blueprint, o novo guia de decisão, o roadmap fortalecido, a nova camada de modelo de gestão do trabalho e mission control, a visão mais orientada à experiência de produto da interface, o PRD conceitual consolidando a visão do produto e agora o conjunto inicial de ADRs estratégicas, o pacote passa a apoiar melhor tanto decisões de platform architecture quanto decisões de operação humana e definição de produto, ainda sem entrar em implementação. O pacote permanece deliberadamente não implementacional: não há protótipo, automação executável ou especificação técnica final nesta fase.

# Backlog de decisões arquiteturais

## Objetivo
Registrar as decisões arquiteturalmente significativas que a próxima fase precisa fechar, refinar ou manter em aberto de forma explícita, preservando continuidade com os ADRs já criados.

## Resposta curta
O repositório já fixou algumas direções estruturantes. O backlog de decisões agora serve para evitar dois erros: fingir que tudo já está resolvido ou reabrir sem necessidade o que já ficou suficientemente sustentado.

## Decisões praticamente estabelecidas

## 1. Postura control-plane-first
### Status
Fortemente estabelecida.

### Base
A coordenação, o estado canônico, policy, approvals, evidência e identidade do trabalho devem residir fora do runtime cognitivo.

### Próximo passo
Traduzir isso em visões e contratos de design mais explícitos.

## 2. Workflow backbone durável
### Status
Fortemente estabelecida.

### Base
Long-running work, waits, retries, branching e retomada confiável pedem backbone próprio.

### Próximo passo
Explicitar melhor a fronteira entre workflow backbone e control plane.

## 3. Governança human-in-the-loop
### Status
Fortemente estabelecida.

### Base
Supervisão humana é primitive de plataforma em etapas críticas.

### Próximo passo
Detalhar melhor matriz de autonomia por risco e reversibilidade.

## 4. Especialistas e runtimes pluggable
### Status
Fortemente estabelecida.

### Base
O núcleo próprio da plataforma não deve ficar preso ao especialista do momento.

### Próximo passo
Definir melhor contratos estáveis entre control plane, runtime e integrações.

## 5. Evidência e auditabilidade como primeira classe
### Status
Fortemente estabelecida.

### Base
Decisões críticas precisam ser explicáveis e sustentadas por trilha verificável.

### Próximo passo
Descrever o modelo conceitual mínimo de evidence, decision trail e exception trail.

## 6. UI como mission control
### Status
Fortemente estabelecida.

### Base
A experiência operacional da plataforma não pode ser reduzida a chat.

### Próximo passo
Conectar melhor objetos de domínio a superfícies da UI.

## Decisões abertas prioritárias

## A. Fronteira exata entre control plane e workflow backbone
### Por que importa
Sem essa separação, há risco de duplicar responsabilidades ou criar acoplamento confuso entre coordenação semântica e execução durável.

### Opções em disputa
- control plane mais espesso, workflow mais subordinado
- workflow backbone mais rico, com parte da semântica operacional embutida

### Critério dominante
Preservar legibilidade do trabalho e governança sem perder robustez operacional.

## B. Granularidade do modelo canônico de objetos
### Por que importa
Objetos demais geram burocracia. Objetos de menos geram opacidade.

### Opções em disputa
- modelo mais minimalista, centrado em mission, workflow, task, artifact e evidence
- modelo mais explícito, incluindo handoff, review, approval, exception e policy como first-class

### Recomendação provisória
Manter explicitamente os objetos ligados a governança e transição crítica.

## C. Modelo de policy e alçadas
### Por que importa
Boa parte da diferenciação estratégica da plataforma está em como autonomia é modulada por risco.

### Perguntas abertas
- policy fica declarada por missão, por task ou por capability?
- approvals são dirigidos por tipo de ação, criticidade ou domínio?
- exceções reabrem política ou apenas escalam decisão?

## D. Estratégia de memória por tipo e retenção
### Por que importa
A plataforma precisa de contexto rico sem virar acúmulo opaco e sensível de dados.

### Perguntas abertas
- o que é memória operacional versus institucional?
- qual informação precisa ser retida como evidence?
- que dados podem ser efêmeros?

## E. Desenho do integration gateway
### Por que importa
Integrações são onde a plataforma toca o mundo real do SDLC.

### Perguntas abertas
- quais capacidades devem ser abstraídas por contratos canônicos?
- onde termina a abstração comum e começa a especificidade por ferramenta?
- como preservar autorização contextual por etapa?

## F. Pacote mínimo de documentação da próxima fase
### Por que importa
Sem escopo editorial claro, a próxima fase corre risco de produzir documentação volumosa porém pouco útil.

### Recomendação provisória
Começar por contexto, contêineres conceituais, fluxos críticos, cenários de qualidade, domínio conceitual e ADRs incrementais.

## Dependências entre decisões
### Proposta conceitual
- a fronteira entre control plane e workflow backbone influencia o modelo de domínio
- o modelo de domínio influencia visões, mission control e trilha de evidência
- policy e alçadas influenciam fluxos dinâmicos e qualidade arquitetural
- estratégia de memória influencia segurança, auditabilidade e custo
- integration gateway influencia extensibilidade e operação real no SDLC

## Como o backlog se relaciona com ADRs
### Regra editorial
- usar **ADR** quando a direção já estiver suficientemente madura
- usar **decision backlog** quando ainda houver alternativa real, critério em disputa ou dependência relevante

## Conclusão
### Recomendação
O backlog da próxima fase deve ser pequeno, explícito e vivo. O objetivo não é listar tudo o que alguém poderia decidir, mas concentrar o foco nas escolhas que realmente definem a forma da plataforma.

## Referências
- ADR project: https://adr.github.io/
- Microsoft Learn, architecture decision record: https://learn.microsoft.com/en-us/azure/well-architected/architect-role/architecture-decision-record
- `docs/90-adrs/README.md`
- `docs/90-adrs/ADR-001-control-plane-first-posture.md`
- `docs/90-adrs/ADR-002-mission-workflow-task-object-model.md`
- `docs/90-adrs/ADR-003-human-in-the-loop-governance.md`
- `docs/90-adrs/ADR-004-compositional-stack-strategy.md`
- `docs/90-adrs/ADR-006-evidence-and-auditability-first-class.md`

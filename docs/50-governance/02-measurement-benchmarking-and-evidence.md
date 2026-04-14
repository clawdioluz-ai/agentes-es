# Medição, benchmarking e modelo de evidência para orquestração com IA

## Objetivo
Definir como avaliar um sistema de orquestração de desenvolvimento com IA sem reduzir o problema a velocidade de geração de código.

## Problema
### Fatos observados
- GitHub discute explicitamente que produtividade de desenvolvedores é multidimensional e usa o framework SPACE para orientar pesquisa e interpretação de resultados. Fonte: GitHub Blog, 2022, https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/
- Microsoft Research reporta ganho de 55,8% em tempo de conclusão num experimento controlado com tarefa específica de implementação. Fonte: Microsoft Research, 2023, https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/
- DORA descreve um core model baseado em capacidades, métricas e outcomes repetidamente demonstrados na pesquisa. Fonte: DORA Research, 2026, https://dora.dev/research/
- SWE-bench mantém benchmark oficial de resolução de issues reais em repositórios open source, com leaderboards públicos. Fonte: SWE-bench, 2026, https://www.swebench.com/

### Inferência
Nenhuma dessas abordagens, isoladamente, mede o desempenho de um sistema de orquestração ponta a ponta em ambiente corporativo. Elas cobrem pedaços distintos do problema.

## Quatro camadas de avaliação

### 1. Métricas de fluxo
#### Proposta conceitual
Medem se o sistema orquestra bem o trabalho.
- lead time por fluxo e por etapa
- tempo até primeira saída utilizável
- taxa de bloqueio por dependência
- taxa de handoff concluído sem retrabalho
- tempo em espera por checkpoint humano

### 2. Métricas de qualidade
#### Proposta conceitual
Medem se a saída final e intermediária é confiável.
- aderência do output ao contrato
- cobertura de testes exigidos
- densidade de defeitos por mudança
- regressões detectadas pós-merge ou pós-release
- taxa de rollback ou hotfix

### 3. Métricas de governança e risco
#### Proposta conceitual
Medem se o sistema permanece controlável.
- violações de policy por fluxo
- exceções aprovadas por tipo de risco
- uso de contexto sensível por etapa
- percentual de decisões com evidência insuficiente
- incidentes ligados a automação ou baixa revisão

### 4. Métricas de economia operacional
#### Proposta conceitual
Medem custo sistêmico, não apenas velocidade local.
- esforço humano poupado e esforço humano deslocado
- custo computacional por fluxo
- custo por artefato aceito
- retrabalho induzido por saídas de baixa qualidade
- custo de supervisão por faixa de risco

## Tipos de benchmark que devem coexistir

### Benchmark A, microtarefa controlada
#### Fato observado
Experimentos como o da Microsoft Research são úteis para medir efeitos causais em tarefas delimitadas.

#### Limitação
Generalizam mal para fluxos multietapa e fortemente dependentes de contexto organizacional.

### Benchmark B, benchmark externo de resolução de issues
#### Fato observado
SWE-bench compara agentes em problemas reais de engenharia de software.

#### Limitação
É útil para capacidade de resolução técnica, mas ainda não mede governança, aprovação, handoff interequipes, compliance e operação em produção.

### Benchmark C, telemetria de produto em uso real
#### Fato observado
GitHub usa feedback em produção, taxa de resolução antes do merge e outros sinais para evoluir o code review agent.

#### Limitação
Esses dados podem refletir produto específico, população específica e incentivos de plataforma.

### Benchmark D, métrica sistêmica de software delivery
#### Fato observado
DORA trata capacidades e outcomes de delivery como sistema.

#### Limitação
DORA não foi criado especificamente para medir agentes, então precisa ser estendido para autonomia, evidência e escalonamento humano.

## Extensão proposta para avaliação de orquestração com IA

### Proposta conceitual
Adicionar ao baseline DORA e SPACE uma camada própria de orquestração:
- taxa de completude de contexto por etapa
- taxa de conformidade de handoff
- taxa de conflito entre especialistas
- taxa de escalonamento humano por risco
- tempo para resolver exceções
- porcentagem de decisões materiais com evidência auditável
- confiança declarada vs resultado observado

## Regras metodológicas

### Proposta conceitual
1. Nunca usar apenas linhas de código, velocidade de geração ou número de tickets fechados como proxy central.
2. Medir outputs intermediários, não só release final.
3. Separar claramente produtividade percebida de produtividade causal.
4. Medir qualidade e risco com a mesma prioridade da velocidade.
5. Registrar quando o humano corrigiu, reviu ou anulou o agente.
6. Tratar ausência de evidência como achado, não como neutro.

## Matriz resumida de evidência

| Tipo de evidência | O que prova melhor | O que prova mal |
|---|---|---|
| Experimento controlado | efeito causal em tarefa específica | desempenho sistêmico no SDLC |
| Benchmark externo | capacidade comparativa em tarefa padronizada | governança e contexto empresarial |
| Telemetria de produto | uso real e comportamento em escala | causalidade limpa e portabilidade |
| Métricas de fluxo | desempenho operacional fim a fim | causalidade sem desenho experimental |
| Revisão humana e auditoria | aderência, risco e explicabilidade | escala automática isoladamente |

## Conclusão
### Inferência
O erro mais provável de programas de agentic software engineering será confundir benchmark local com maturidade operacional.

### Proposta conceitual
Este repositório deve sustentar uma avaliação combinada, causal quando possível, operacional sempre, e auditável por padrão.
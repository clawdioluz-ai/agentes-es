# Decisão de stack para a plataforma de orquestração de Murilo

## Objetivo
Criar uma leitura decisória, em nível conceitual, sobre quais combinações de stack fazem mais sentido para uma plataforma cujo problema central é **orquestração governada**, e não apenas execução de agentes isolados.

## Como ler este documento
- **Fato observado**: sustentado por fontes já curadas neste repositório.
- **Inferência**: síntese comparativa para apoiar decisão.
- **Recomendação de desenho futuro**: direção sugerida para a próxima fase.

## Resposta curta
### Recomendação de desenho futuro
A melhor direção agora é uma arquitetura **control-plane-first e composicional**, com:
- **OpenClaw** como camada de control plane local-first, sessões, superfícies operacionais e roteamento
- **Temporal** como backbone de workflow durável
- **OpenAI Agents SDK** ou **LangGraph** como runtime cognitivo subordinado
- **Langfuse** como camada inicial de observabilidade e avaliação

### Inferência
Essa direção é a que melhor preserva os objetivos do repositório: baixa dependência de um único fornecedor, boa postura local-first, separação forte entre coordenação e execução, governança explícita e espaço para evoluir sem recomeçar a arquitetura.

## Critérios de decisão
### Proposta conceitual
As opções abaixo são comparadas pelos critérios mais relevantes para a plataforma desejada:
- aderência ao problema de orquestração
- separação entre control plane, workflow e runtime de agentes
- risco de acoplamento
- extensibilidade
- prontidão para governança
- observabilidade
- postura local-first
- proporção entre construir versus compor

## Opção 1, OpenClaw + Temporal + OpenAI Agents SDK + Langfuse

### Fit
### Inferência
É a opção mais alinhada quando o centro de gravidade da plataforma é **coordenação operacional governada**, com múltiplas superfícies, sessões, tools, checkpoints humanos e fluxos longos.

### Forças
- OpenClaw já encaixa bem como control plane e camada operacional local-first.
- Temporal oferece durabilidade forte, waits longos, retries, compensação e retomada confiável.
- OpenAI Agents SDK traz primitives relativamente pequenas para agentes, handoffs, guardrails, sessões e tracing, o que ajuda a manter a camada cognitiva mais contida.
- Langfuse reduz lock-in na observabilidade e cobre tracing, sessões, agent graphs e avaliação inicial.

### Fraquezas
- É uma composição mais deliberada e menos “pronta de fábrica”.
- Exige disciplina arquitetural maior para contratos entre camadas.
- Pode parecer mais pesada no início do que stacks mais opinadas ou visuais.

### Risco de acoplamento
### Inferência
**Baixo a médio.** O principal risco é a cola entre camadas, não o domínio completo por um único framework. Isso é aceitável porque o acoplamento fica mais sob controle do time.

### Extensibilidade
### Inferência
**Alta.** Permite trocar runtime cognitivo, observabilidade e até partes do workflow sem desmontar a identidade da plataforma.

### Prontidão para governança
### Inferência
**Alta.** A separação entre control plane, workflow e runtime favorece approvals, alçadas, auditoria e segregação de funções.

### Observabilidade
### Inferência
**Alta**, especialmente se tracing e evidência forem tratados desde o início como objetos de primeira classe.

### Postura local-first
### Inferência
**Alta.** OpenClaw puxa a arquitetura para operação local-first e híbrida com mais naturalidade do que stacks mais SaaS-first.

### Build vs compose
### Inferência
A direção correta aqui é **compor o backbone e construir a governança específica**. Não vale construir engine de workflow nem observabilidade do zero.

### Leitura final
### Inferência
É a opção mais forte para uma plataforma própria, diferenciada por orquestração, governança e flexibilidade estrutural.

## Opção 2, OpenClaw + LangGraph + Langfuse ou LangSmith

### Fit
### Inferência
É uma boa opção quando Murilo quiser manter a arquitetura mais próxima de um runtime stateful agentic, com menos fragmentação inicial e mais velocidade para explorar fluxos complexos com memória, branching e human-in-the-loop.

### Forças
- Mantém OpenClaw na posição certa de control plane operacional.
- LangGraph é forte para agentes stateful, durable execution, memória e interrupções humanas.
- A modelagem de grafos favorece fluxos ricos, handoffs e lógica de orquestração cognitiva mais explícita.
- Langfuse ou LangSmith complementam bem tracing e avaliação.

### Fraquezas
- A fronteira entre workflow durável e runtime de agentes fica mais próxima, o que pode embaralhar responsabilidades ao longo do tempo.
- O ecossistema LangChain pode introduzir mais acoplamento conceitual e operacional do que parece no início.
- Há risco de a plataforma passar a “pensar em LangGraph” demais, em vez de pensar em contratos neutros de fluxo.

### Risco de acoplamento
### Inferência
**Médio.** Melhor que escolher um framework de equipe mais fechado como centro da arquitetura, mas mais arriscado do que combinar OpenClaw com um workflow backbone mais neutro como Temporal.

### Extensibilidade
### Inferência
**Média a alta.** É extensível, mas a evolução pode acabar orbitando demais o modelo de grafo e o ecossistema ao redor.

### Prontidão para governança
### Inferência
**Média a alta.** Há boas primitives para human-in-the-loop e estado, mas a governança sistêmica ainda depende fortemente de disciplina fora do runtime.

### Observabilidade
### Inferência
**Alta** com Langfuse ou LangSmith, mas a qualidade real dependerá de manter separação entre trace técnico e evidência decisória.

### Postura local-first
### Inferência
**Média a alta.** Funciona bem em operação própria, mas não puxa local-first tão fortemente por si só quanto OpenClaw.

### Build vs compose
### Inferência
Aqui faz sentido **compor bastante e construir menos no começo**, desde que os contratos de fluxo não fiquem implícitos no framework.

### Leitura final
### Inferência
É a melhor opção se a prioridade imediata for experimentar rápido com orquestração stateful de agentes sem ainda assumir o peso completo de um backbone como Temporal.

## Opção 3, Langflow + OpenAI Agents SDK ou CrewAI + Prefect + Langfuse

### Fit
### Inferência
É uma opção razoável quando o objetivo principal é acelerar composição, prototipação visual e demonstração de fluxos, sem ainda otimizar a arquitetura para rigor máximo de governança.

### Forças
- Langflow acelera desenho visual, experimentação e composição de flows.
- Prefect oferece estado, pausas, automações por eventos e operação relativamente amigável.
- Agents SDK ou CrewAI podem preencher a camada de especialistas com velocidade inicial.
- O conjunto é didático e útil para explorar fluxos com stakeholders.

### Fraquezas
- O centro de gravidade pode escorregar para prototipação em vez de plataforma.
- A camada visual tende a ser ótima para descoberta, mas menos convincente como espinha dorsal de governança crítica.
- CrewAI traz risco de narrativa de “equipes de agentes” dominar a arquitetura acima dos contratos e handoffs.
- Prefect é forte, mas menos naturalmente posicionado como núcleo de missão crítica de longa duração do que Temporal.

### Risco de acoplamento
### Inferência
**Médio a alto.** Especialmente se a semântica do fluxo acabar embutida demais na ferramenta visual ou no framework de crews.

### Extensibilidade
### Inferência
**Média.** Boa para crescer até certo ponto, mas pode exigir reestruturação quando governança, escala e clareza de fronteiras ficarem mais exigentes.

### Prontidão para governança
### Inferência
**Média.** Dá para montar aprovações e trilhas, mas a plataforma tende a exigir mais cuidado para não ficar cosmeticamente governada.

### Observabilidade
### Inferência
**Média a alta** com Langfuse, porém a clareza do que é trace, estado de fluxo e evidência operacional pode degradar se o stack crescer de forma orgânica demais.

### Postura local-first
### Inferência
**Média.** Pode operar fora de SaaS, mas não nasce com a mesma vocação local-first de OpenClaw.

### Build vs compose
### Inferência
É a opção mais orientada a **compor quase tudo**, o que acelera aprendizado, mas reduz nitidez arquitetural se virar decisão permanente.

### Leitura final
### Inferência
Boa para fase de exploração e design discovery. Fraca como direção principal se o objetivo real já é uma plataforma de orquestração durável e governável.

## Opção 4, stack centrado em framework de equipes, AutoGen ou CrewAI como núcleo, com observabilidade acoplada

### Fit
### Inferência
É a opção menos indicada se o objetivo é construir uma plataforma de orquestração, porque desloca o centro da arquitetura para o runtime multiagente em si.

### Forças
- Rápida para colocar múltiplos agentes interagindo.
- Boa para provar conceitos de colaboração entre especialistas.
- Pode gerar demos impressionantes cedo.

### Fraquezas
- Tende a misturar coordenação, execução, memória e policy num mesmo plano lógico.
- Handoffs podem virar convenção do framework, não contrato de plataforma.
- Governança, approvals e trilha auditável costumam precisar ser adicionadas “por fora”.
- O risco de confundir comportamento emergente com arquitetura sólida é alto.

### Risco de acoplamento
### Inferência
**Alto.** O modelo mental do framework tende a capturar a plataforma inteira.

### Extensibilidade
### Inferência
**Média.** Dá para evoluir, mas muitas vezes a evolução passa por contornar o framework em vez de usá-lo como base estável.

### Prontidão para governança
### Inferência
**Baixa a média.** Não porque seja impossível, mas porque a governança entra como correção posterior, não como centro estrutural.

### Observabilidade
### Inferência
**Média.** Pode ser instrumentada, mas frequentemente a observabilidade nasce mais como debug técnico do que como evidência decisória.

### Postura local-first
### Inferência
**Variável.** Não é a principal vantagem desse caminho.

### Build vs compose
### Inferência
Parece uma opção de alta composição, mas na prática frequentemente leva a **reconstruir governança e controle em volta** do framework.

### Leitura final
### Inferência
Vale como laboratório de padrões multiagente, não como espinha dorsal da plataforma.

## Comparação resumida

| Opção | Fit para orquestração | Acoplamento | Extensibilidade | Governança | Observabilidade | Local-first | Build vs compose |
|---|---|---|---|---|---|---|---|
| OpenClaw + Temporal + Agents SDK + Langfuse | muito alto | baixo-médio | alto | alto | alto | alto | compor backbone, construir governança específica |
| OpenClaw + LangGraph + Langfuse/LangSmith | alto | médio | média-alta | média-alta | alto | média-alta | compor bastante, com cuidado aos contratos |
| Langflow + Prefect + Agents SDK/CrewAI + Langfuse | médio | médio-alto | média | média | média-alta | média | compor quase tudo |
| AutoGen ou CrewAI como núcleo principal | baixo-médio | alto | média | baixa-média | média | variável | parece compor, mas empurra reconstrução ao redor |

## O que compor e o que construir
### Recomendação de desenho futuro
Murilo não deveria tentar construir do zero:
- engine de workflow durável
- runtime genérico de agentes
- stack base de tracing e observabilidade
- primitives de pausa, retomada e retries

### Recomendação de desenho futuro
Murilo deveria concentrar construção própria em:
- modelo de fluxo e contratos
- identidade do handoff
- política e alçadas de autonomia
- evidência, decisão e escalonamento
- integração semântica com artefatos do SDLC
- camada de governança que sobreviva à troca de runtimes

## Recomendação final
### Recomendação de desenho futuro
Escolher agora a direção **OpenClaw + Temporal + runtime cognitivo subordinado + Langfuse**.

### Por quê
### Inferência
Porque esta é a combinação que melhor equilibra:
- controle arquitetural sem reinventar infraestrutura pesada
- forte aderência à tese de control plane do repositório
- menor risco de capturar a plataforma inteira dentro de um framework de agentes
- melhor prontidão para governança, auditoria e checkpoints humanos
- melhor postura para evolução local-first e híbrida
- melhor chance de Murilo construir diferencial na camada certa, a de orquestração, e não na reinvenção de blocos já maduros

### Escolha tática dentro dessa direção
### Recomendação de desenho futuro
Se Murilo quiser reduzir complexidade inicial, a variante mais pragmática é:
- começar com **OpenClaw + LangGraph + Langfuse** como composição mais enxuta de exploração
- mantendo a arquitetura pensada para migrar o backbone de durabilidade para **Temporal** quando a plataforma exigir workflows mais longos, críticos e auditáveis

### Decisão orientadora
### Recomendação de desenho futuro
Portanto, a decisão recomendada não é “qual framework de agentes usar?”. A decisão correta agora é: **adotar uma arquitetura composicional em que o control plane manda, o workflow backbone preserva durabilidade, e o runtime de agentes permanece substituível**.

## Nível de confiança
### Inferência
**Confiança: média-alta.** A direção geral é fortemente sustentada pelo benchmark do repositório e pela comparação entre classes de ferramentas. A confiança cai em preferências finas entre runtimes cognitivos, porque esse espaço evolui rápido e depende do estilo de operação que Murilo quiser priorizar primeiro.

## Referências principais
- OpenClaw README e Gateway docs
- LangGraph docs
- Temporal docs
- Prefect docs
- OpenAI Agents SDK docs
- AutoGen docs
- CrewAI docs
- Langflow docs
- Langfuse docs
- LangSmith docs
- GitLab Duo / Agentic SDLC materials

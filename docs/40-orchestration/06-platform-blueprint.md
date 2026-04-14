# Platform blueprint, north star architecture for Murilo's orchestration platform

## Objetivo
Consolidar, em um único documento orientador, a forma recomendada da plataforma futura. Este blueprint liga a pesquisa, a proposta de arquitetura-alvo e a decisão de stack em uma visão coerente de produto e plataforma. O foco continua conceitual: definir o que a plataforma precisa ser, o que deve permanecer pluggable, em que ordem ela deve evoluir e quais princípios devem governar as escolhas.

## Tese central
### Proposta conceitual
A plataforma de Murilo deve ser pensada como uma **plataforma de orquestração governada para software delivery**, não como um conjunto de agentes especialistas conectados entre si.

### Inferência
O diferencial estratégico não está em possuir o especialista mais sofisticado, mas em possuir a camada que:
- entende o fluxo ponta a ponta
- governa handoffs, evidências, risco e autonomia
- aciona especialistas e ferramentas sob contrato
- mantém supervisão humana onde ela é obrigatória
- preserva modularidade para evoluir sem reescrever a plataforma

## North star
### Proposta conceitual
A arquitetura north star é **control-plane-first, workflow-backed, runtime-agnostic e policy-governed**.

Em termos simples:
- o **control plane** é o centro administrativo do sistema
- o **workflow backbone** garante durabilidade operacional
- o **runtime cognitivo** executa trabalho especializado, mas não governa a plataforma
- a **governança** atravessa todo o sistema
- **memória, evidência e observabilidade** são capacidades de primeira classe
- integrações com o SDLC entram por contratos, não por acoplamentos ad hoc

## Forma recomendada da plataforma

## 1. Camada obrigatória, surfaces and flow intake
### Papel
Receber trabalho, iniciar fluxos, mostrar estado e permitir intervenção.

### Deve incluir
- superfícies de entrada, como chat, issues, PRs, pipelines e APIs
- catálogo visível de fluxos ou capacidades
- visão operacional do status do fluxo
- pontos claros para aprovação, exceção e escalonamento

### Regra
A experiência de entrada não pode ser o centro semântico da plataforma. Canais mudam, o fluxo governado permanece.

## 2. Camada obrigatória, control plane
### Papel
Ser o sistema de registro do trabalho agentic.

### Deve incluir
- identidade de fluxo e suas revisões
- classificação de risco, criticidade e ownership
- seleção de políticas aplicáveis
- despacho para workflow, especialistas e integrações
- registro de decisões, handoffs, evidências e exceções
- coordenação de aprovações e escalonamentos

### Regra
Tudo o que for crítico para coordenação, governança e auditabilidade deve passar pelo control plane.

## 3. Camada obrigatória, workflow backbone durável
### Papel
Sustentar a execução longa e confiável do trabalho.

### Deve incluir
- estado persistente do fluxo
- waits, retries, branching, joins e compensações
- pausa para aprovação humana
- retomada após falhas ou eventos externos

### Regra
Durabilidade não deve depender da memória conversacional de um agente nem do contexto efêmero do LLM.

## 4. Camada obrigatória, runtime de especialistas
### Papel
Executar etapas cognitivas delimitadas por contrato.

### Deve incluir
- especialistas ou skills substituíveis
- acesso controlado a ferramentas
- saída estruturada por contrato de etapa
- declaração de confiança, lacunas e necessidade de escalonamento

### Regra
O especialista executa, mas não governa o sistema. Ele é subordinado ao fluxo, às políticas e aos limites definidos fora dele.

## 5. Camada obrigatória, context and memory fabric
### Papel
Entregar o contexto certo, na hora certa, com governança.

### Deve incluir
- estado operacional do fluxo
- memória de trabalho local da execução
- retrieval de conhecimento recuperável
- memória institucional e normativa
- proveniência, escopo, sensibilidade e retenção

### Regra
Memória não é um bloco único. A plataforma deve separar claramente contexto operacional, conhecimento e memória institucional.

## 6. Camada obrigatória, policy and approval fabric
### Papel
Aplicar alçadas, limites de autonomia e checkpoints humanos.

### Deve incluir
- matriz de autonomia por risco e reversibilidade
- regras de segregação de funções
- aprovações obrigatórias em transições críticas
- controle de acesso, secrets e boundaries de dados
- justificativa e trilha para exceções

### Regra
Governança não pode ser um detalhe de fluxo local. Ela precisa ser transversal e explícita.

## 7. Camada obrigatória, observability, evidence and evaluation
### Papel
Explicar o que aconteceu, por que aconteceu e quão bem funcionou.

### Deve incluir
- tracing por fluxo, etapa, ferramenta e especialista
- custos, latência e uso de modelos
- evidências que sustentam decisões materiais
- métricas operacionais e de qualidade
- avaliação online e offline

### Regra
A plataforma deve nascer capaz de ser auditada, comparada e melhorada. Sem isso, ela será só automação opaca.

## 8. Camada obrigatória, integration gateway
### Papel
Conectar a plataforma aos sistemas reais do SDLC.

### Deve incluir
- integração com git, PR/MR, CI/CD, testes, docs, backlog, observability e incident tools
- catálogo de ferramentas com contratos claros
- controle de autenticação e autorização por ferramenta e etapa

### Regra
Integrações devem ser tratadas como interfaces de plataforma, não como detalhes escondidos em prompts.

## Componentes opcionais, mas desejáveis
### Proposta conceitual
Os componentes abaixo não precisam existir no primeiro incremento, mas fazem sentido como extensões da north star:
- marketplace ou catálogo de especialistas e fluxos
- simulador ou sandbox de políticas e autonomia
- replay e comparação de execuções para avaliação
- camada de recomendação de rota, especialista ou política
- memória institucional alimentada por pós-mortem, incidentes e resultados
- suporte multi-tenant mais amplo
- engine de experimentação para prompts, policies e modelos
- camada de produto para self-service governado por times internos

## O que deve permanecer pluggable
### Recomendação de desenho futuro
Para preservar flexibilidade e evitar lock-in estrutural, os seguintes blocos devem permanecer substituíveis:
- runtime cognitivo de agentes
- fornecedores de modelo
- observabilidade e evaluation stack
- conectores de workflow, desde que respeitem contratos do control plane
- mecanismos de retrieval e embeddings
- conectores de sistemas do SDLC
- políticas específicas por domínio, desde que usem interfaces comuns

### Inferência
A plataforma não deve ficar refém da ferramenta que hoje executa melhor o raciocínio. O valor próprio está na coordenação, nos contratos e na governança.

## O que vale consolidar como núcleo próprio
### Recomendação de desenho futuro
Os ativos que merecem consolidação como IP da plataforma são:
- modelo de fluxo e identidade do trabalho
- contratos de etapa, handoff, evidência, aprovação e exceção
- matriz de autonomia por risco
- política operacional ligada ao contexto do negócio
- lógica de despacho entre fluxos, especialistas e controles
- integração semântica entre artefatos do SDLC, evidência e decisão
- trilha canônica de governança e auditabilidade

## Sequência de evolução recomendada

## Fase 1, fundação operacional governada
### Objetivo
Criar o menor sistema que já se comporte como plataforma de orquestração, mesmo com poucos fluxos.

### Construir primeiro
- control plane mínimo
- contrato de fluxo e contrato de etapa
- backbone durável para waits, retries e approvals
- poucos especialistas de alto valor, claramente delimitados
- integração inicial com superfícies principais, como chat e git
- evidência e tracing mínimos desde o início
- matriz simples de autonomia por risco

### Resultado esperado
A plataforma já consegue coordenar um fluxo real com identidade, governança, checkpoints humanos e trilha de evidência.

## Fase 2, composição end-to-end por domínios do SDLC
### Objetivo
Expandir de fluxos isolados para jornadas compostas.

### Adicionar
- handoffs formais entre especialistas
- contratos de evidência e aprovação mais ricos
- mais integrações de SDLC, como backlog, CI/CD, docs e testes
- taxonomia de fluxos e especialistas
- avaliação operacional comparável entre fluxos

### Resultado esperado
A plataforma deixa de parecer um conjunto de automações e passa a operar como backbone de coordenação de várias etapas do delivery.

## Fase 3, governança adaptativa e escala organizacional
### Objetivo
Escalar a plataforma sem perder controle.

### Adicionar
- políticas por domínio, time ou criticidade
- multi-team e multi-tenant mais explícito
- aprendizado a partir de execução, exceções e resultados
- capacidades de benchmarking interno
- catálogo mais amplo de fluxos reutilizáveis

### Resultado esperado
A plataforma se torna um sistema de operação organizacional, e não apenas uma camada de produtividade.

## Fase 4, plataforma adaptativa sem perder supervisão humana
### Objetivo
Aumentar autonomia com guardrails melhores, não com confiança cega.

### Adicionar
- calibragem contínua de autonomia
- rotas dinâmicas com base em risco e evidência
- mecanismos de replay, comparação e melhoria contínua
- memória institucional alimentando desenho de políticas e fluxos

### Resultado esperado
A plataforma aprende com execução real, mas continua governada por contratos, evidência e checkpoints humanos.

## O que não construir primeiro
### Recomendação de desenho futuro
Murilo não deveria começar por:
- uma grande biblioteca de especialistas antes de definir contratos
- memória ampla e difusa sem modelo de proveniência
- UX sofisticada antes de estabilizar o núcleo de coordenação
- automação total de ponta a ponta sem política e approvals maduros
- reimplementar workflow engine, tracing ou runtime genérico do zero

### Inferência
Começar pelos blocos errados geraria demonstrações impressionantes, mas uma base frágil para uma plataforma real.

## Produto e plataforma, relação recomendada
### Proposta conceitual
O produto visível deve emergir da plataforma, não substituí-la.

Isso significa:
- o usuário enxerga jornadas, status, exceções e valor entregue
- a plataforma sustenta identidade, contratos, policy, evidência e interoperabilidade
- novas experiências de uso devem reutilizar o mesmo núcleo governado

### Regra
Não criar um produto conversacional que esconda a arquitetura, nem uma plataforma tão abstrata que nunca apareça como experiência útil.

## Princípios arquiteturais orientadores
1. **control plane acima de runtime**
2. **durabilidade fora do loop puro do agente**
3. **contratos antes de convenções implícitas**
4. **governança orientada a risco e reversibilidade**
5. **human-in-the-loop como primitive, não exceção**
6. **memória particionada por função e proveniência**
7. **evidência antes de confiança implícita**
8. **observabilidade desde o início**
9. **compor commodities, construir diferenciação**
10. **plugabilidade sem perda de identidade arquitetural**
11. **integração semântica com o SDLC real**
12. **evolução incremental sem trair a north star**

## Leitura da stack recomendada dentro do blueprint
### Proposta conceitual
A decisão de stack já apontada no repositório continua coerente com este blueprint:
- **OpenClaw** como camada operacional e de control plane local-first
- **Temporal** como backbone preferencial de workflow durável
- **OpenAI Agents SDK** ou **LangGraph** como runtime cognitivo subordinado
- **Langfuse** como base inicial de tracing e avaliação

### Inferência
O ponto central não é a ferramenta específica, mas o fato de que a pilha respeita a hierarquia correta: coordenação e governança acima, execução cognitiva abaixo.

## Decisão orientadora final
### Recomendação de desenho futuro
A plataforma de Murilo deve ser construída como um **sistema de orquestração governada para software delivery**, em que o núcleo próprio está na identidade do fluxo, nos contratos, na política, na evidência e na coordenação entre especialistas, ferramentas e humanos.

### Inferência
Se essa north star for respeitada, Murilo poderá evoluir de fluxos assistidos para uma plataforma adaptativa sem ficar preso a um framework de agentes, a uma interface específica ou a um único fornecedor. Esse é o caminho mais coerente com a pesquisa deste repositório e com a ambição de construir uma plataforma, não apenas uma demo agentic.

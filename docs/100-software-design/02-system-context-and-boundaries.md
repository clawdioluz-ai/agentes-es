# Contexto do sistema e fronteiras

## Objetivo
Delimitar, em nível conceitual, o sistema que esta pesquisa propõe, separando núcleo próprio de plataforma, superfícies operacionais, capacidades transversais e ecossistema externo do SDLC.

## Resposta curta
A plataforma proposta não é um agente único, nem apenas uma interface conversacional. Ela é um **sistema de coordenação governada do trabalho agentic de software delivery**. Seu núcleo próprio fica no control plane e nas capacidades que sustentam fluxo, política, memória, evidência e supervisão humana.

## Sistema de interesse
### Definição
O sistema de interesse é uma **plataforma de orquestração governada para software delivery assistido por IA**, capaz de:
- receber trabalho por diferentes superfícies
- transformar intenção em fluxo governado
- coordenar especialistas e ferramentas do SDLC
- aplicar políticas e aprovações
- manter estado, evidência e rastreabilidade
- tornar o trabalho observável para operadores humanos

## Fronteira do núcleo próprio
### Dentro do núcleo conceitual
1. **Mission control UI**
   - portfolio de missões
   - mission detail
   - review e approval surfaces
   - observability cockpit

2. **Control plane**
   - identidade canônica do trabalho
   - estado agregado
   - classificação de risco
   - contratos de etapa e handoff
   - despacho e coordenação

3. **Workflow backbone durável**
   - waits
   - retries
   - branching
   - compensação
   - retomada por evento

4. **Runtime de especialistas**
   - execução cognitiva delimitada por contrato
   - uso controlado de ferramentas
   - produção de saídas estruturadas

5. **Context and memory fabric**
   - estado operacional
   - memória de trabalho
   - retrieval governado
   - memória institucional e normativa

6. **Policy and approval fabric**
   - limites de autonomia
   - segregação de funções
   - aprovações obrigatórias
   - enforcement por criticidade

7. **Observability, evidence and evaluation fabric**
   - traces e spans
   - custo e latência
   - evidências de decisão
   - trilha auditável
   - avaliação operacional

8. **Integration gateway**
   - catálogo de integrações
   - autenticação e autorização por ferramenta
   - abstração de sistemas externos do SDLC

## Fora do núcleo, mas estruturalmente relevantes
### Sistemas externos do SDLC
- git hosting e code review
- issue tracking e backlog
- CI/CD e quality gates
- documentação e knowledge bases
- identity providers
- secrets e policy stores
- observability stack externa
- provedores de modelo
- serviços de cloud e runtime

### Regra de fronteira
Esses sistemas não são “detalhes”. Eles são parte do contexto arquitetural, mas não devem redefinir semanticamente o núcleo da plataforma.

## Fronteiras que precisam permanecer pluggable
### Recomendação de desenho futuro
Devem permanecer substituíveis:
- provedores de modelos
- runtimes de especialistas
- ferramentas de workflow, desde que subordinadas ao control plane
- mecanismos de retrieval e embeddings
- conectores de observabilidade
- integrações com sistemas do SDLC

### Inferência
A plataforma preserva valor próprio quando seu núcleo semântico reside em contratos, políticas, objetos de domínio e governança, não em um fornecedor específico.

## Fronteiras que merecem consolidação própria
### Recomendação de desenho futuro
Devem tender a núcleo próprio:
- modelo canônico de mission, workflow, task, handoff, review, approval, artifact e evidence
- lógica de classificação de risco e autonomia
- contratos de etapa, exceção, aprovação e evidência
- registro canônico de estado e decisão
- semântica operacional da mission control

## Tensões de fronteira

## 1. Control plane versus runtime cognitivo
### Risco
Misturar coordenação corporativa com execução cognitiva local.

### Direção
O runtime deve interpretar contratos e executar trabalho. O control plane deve governar identidade, política, estado e transições críticas.

## 2. Núcleo próprio versus integração rica
### Risco
Tentar absorver ferramentas maduras do SDLC como se a plataforma precisasse reimplementar tudo.

### Direção
A plataforma deve orquestrar e tornar legível o trabalho entre sistemas, não duplicar todo o ecossistema de delivery.

## 3. Mission control versus chat
### Risco
Reduzir operação da plataforma a conversa textual.

### Direção
Chat pode ser uma superfície de entrada e colaboração, mas a plataforma precisa de superfícies explícitas para estado, review, approval, evidência e exceção.

## Conclusão
### Proposta conceitual
A melhor leitura de fronteira para a próxima fase é: **núcleo próprio para coordenação governada, bordas pluggable para execução especializada e ecossistema SDLC**.

## Referências
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/06-platform-blueprint.md`
- `docs/40-orchestration/07-mission-control-ui-and-cockpit.md`
- `docs/30-framework/03-work-management-model.md`
- Team Topologies key concepts: https://teamtopologies.com/key-concepts

# Pilha de artefatos de design

## Objetivo
Definir o pacote mínimo de artefatos de design que a próxima fase deve produzir para transformar a tese do repositório em arquitetura de software comunicável, revisável e governável.

## Resposta curta
A próxima fase não precisa começar por um documento único e monolítico. O pacote mais útil é uma **pilha curta de artefatos complementares**, em que cada item responde a uma pergunta diferente:
1. o que é o sistema e qual fronteira ele ocupa?
2. como ele se organiza estruturalmente?
3. como ele se comporta nos fluxos críticos?
4. quais qualidades precisam ser preservadas?
5. quais decisões são permanentes, provisórias ou ainda abertas?

## Tese de design
### Proposta conceitual
Para esta plataforma, o conjunto de artefatos mais coerente é uma composição pragmática de:
- **visões múltiplas e beyond views**, na linha de *Views and Beyond* do SEI
- **estrutura enxuta e comunicável**, próxima do espírito do arc42
- **diagramas em níveis de abstração**, coerentes com o C4 Model
- **registro contínuo de decisões**, via ADRs e backlog decisório
- **cenários de atributos de qualidade**, para impedir que a arquitetura vire apenas desenho estático

### Inferência
Nenhum desses modelos, isoladamente, resolve o problema do repositório. O ganho vem da combinação: C4 ajuda a explicar forma, ADR ajuda a explicar por que, quality scenarios ajudam a explicar o que não pode quebrar, e uma estrutura tipo arc42 evita dispersão documental.

## Pilha recomendada

## 1. Documento de contexto e fronteiras
### Pergunta que responde
Que sistema está sendo desenhado, para quem, com que limites e em relação a quais sistemas externos?

### Papel
Servir de âncora semântica para todo o restante. Sem ele, cada visão subsequente tende a usar “plataforma”, “orquestrador”, “runtime” e “mission control” com significados ligeiramente diferentes.

### Deve consolidar
- objetivo do sistema
- atores humanos principais
- sistemas externos do SDLC
- fronteiras explícitas do núcleo próprio
- capacidades nativas versus capacidades integradas
- exclusões claras da fase

## 2. Visão estrutural em níveis
### Pergunta que responde
Quais são os grandes blocos da plataforma e como se relacionam?

### Papel
Traduzir a tese control-plane-first em uma forma arquitetural legível.

### Recomendação de desenho futuro
Usar ao menos três níveis conceituais:
- **contexto**: plataforma versus ecossistema
- **contêineres conceituais**: mission control, control plane, workflow backbone, runtime, memory fabric, policy fabric, observability fabric, integration gateway
- **componentes conceituais internos** apenas nos blocos mais críticos, principalmente control plane e governança

## 3. Visões dinâmicas dos fluxos críticos
### Pergunta que responde
Como o sistema se comporta quando trabalho entra, é decomposto, executado, revisado e encerrado?

### Papel
Mostrar comportamento, não só estrutura. Em uma plataforma de orquestração, boa parte do valor está nas transições, handoffs, waits, approvals e exceções.

### Fluxos prioritários
- intake e qualificação de missão
- decomposição em workflow e tasks
- execução com handoffs entre especialistas
- pausa para review ou approval
- tratamento de exceção e escalonamento
- encerramento com evidência e aprendizado

## 4. Cenários de atributos de qualidade
### Pergunta que responde
Quais qualidades arquiteturais são decisivas e como reconhecemos que foram preservadas?

### Papel
Evitar que “governança”, “auditabilidade” e “extensibilidade” permaneçam abstratas.

### Recomendação
Modelar cenários para pelo menos:
- governabilidade
- auditabilidade
- confiabilidade operacional
- segurança e isolamento
- extensibilidade
- observabilidade
- custo operacional e uso eficiente de modelos

## 5. Modelo de domínio conceitual
### Pergunta que responde
Quais objetos o sistema precisa tratar como canônicos para coordenar trabalho e supervisão humana?

### Papel
Conectar arquitetura, operação e produto. O repositório já sugere que mission, workflow, task, handoff, review, approval, artifact e evidence não são detalhes de implementação, mas objetos centrais do control plane.

## 6. Registro de decisões e backlog decisório
### Pergunta que responde
Que direção já está firme, o que ainda está em aberto e quais tradeoffs precisam ser resolvidos?

### Papel
Manter a transição entre pesquisa e desenho como processo cumulativo, e não como reset intelectual.

### Recomendação
Preservar dois mecanismos complementares:
- **ADRs** para decisões já maduras
- **decision backlog** para decisões em aberto, dependências e critérios

## 7. Checklist de revisão de design
### Pergunta que responde
Como revisar o pacote sem cair em preferências subjetivas ou apenas gosto diagramático?

### Papel
Dar disciplina à próxima fase.

### Deve verificar
- coerência com a postura control-plane-first
- separação clara entre coordenação e execução cognitiva
- presença explícita de policy, approval e evidence
- fronteiras pluggable bem delimitadas
- qualidade tratada como cenário, não como slogan

## Ordem recomendada de produção
### Recomendação de desenho futuro
1. contexto e fronteiras
2. visão estrutural de alto nível
3. modelo de domínio conceitual
4. fluxos dinâmicos críticos
5. cenários de qualidade
6. ADRs e backlog decisório atualizados

### Inferência
Essa ordem reduz retrabalho. Ela primeiro estabiliza linguagem e fronteiras, depois forma e comportamento, e só então cristaliza decisões mais específicas.

## O que não vale fazer cedo demais
### Alerta de desenho
A próxima fase deve evitar, cedo demais:
- documentação pseudo-exaustiva de componentes internos ainda hipotéticos
- diagramas técnicos detalhados sem decisões de domínio já estáveis
- pseudo-API design antes de fechar objetos centrais
- deployment design prematuro antes de consolidar qualidade, risco e operação humana

## Conclusão
### Recomendação
O pacote mais adequado para a plataforma é um **design stack enxuto, multi-view e decision-oriented**. Ele deve nascer pequeno, mas suficiente para tornar o sistema inteligível sob três perspectivas simultâneas: arquitetura, operação e governança.

## Referências usadas para esta direção
- SEI, *Documenting Software Architectures: Views and Beyond, 2nd Edition*: https://www.sei.cmu.edu/library/documenting-software-architectures-views-and-beyond-second-edition/
- arc42 documentation: https://arc42.org/documentation/
- C4 Model: https://c4model.com/
- ADR project: https://adr.github.io/
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/06-platform-blueprint.md`
- `docs/90-adrs/README.md`

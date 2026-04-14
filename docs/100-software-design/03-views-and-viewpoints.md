# Visões e viewpoints

## Objetivo
Definir o conjunto mínimo de visões arquiteturais necessário para comunicar a plataforma a públicos diferentes sem perder coerência entre produto, operação, arquitetura e governança.

## Resposta curta
A próxima fase deve adotar um conjunto enxuto de visões, não um diagrama único. A plataforma exige pelo menos cinco viewpoints: **contexto, estrutura, dinâmica, governança e operação humana**.

## Por que múltiplas visões são necessárias
### Fato metodológico
A abordagem *Views and Beyond* parte da ideia de que arquiteturas precisam ser documentadas por um conjunto de visões, complementadas por informações transversais. O C4 Model, por sua vez, fornece níveis úteis de abstração para explicar forma estrutural.

### Inferência
Para esta plataforma, isso significa que um único desenho “de arquitetura” não consegue responder ao mesmo tempo:
- onde está a fronteira do sistema
- como os blocos se relacionam
- como o fluxo se comporta ao longo do tempo
- onde entram políticas e aprovações
- como humanos operam o sistema

## Públicos e perguntas dominantes

| Público | Pergunta dominante | Visão mais útil |
|---|---|---|
| liderança de produto e plataforma | o que estamos construindo e por que esta forma importa? | contexto e estrutura |
| arquitetura | quais são as responsabilidades e fronteiras dos blocos? | estrutura e domínio |
| engenharia de plataforma | onde ficam os pontos de composição e acoplamento? | estrutura e dinâmica |
| governança e segurança | onde entram políticas, alçadas e trilha de evidência? | governança |
| operadores humanos | como acompanhar, revisar, aprovar e escalar trabalho? | operação humana e dinâmica |

## Conjunto mínimo recomendado

## 1. Visão de contexto
### Papel
Mostrar a plataforma no ecossistema maior: usuários, times, sistemas do SDLC, provedores de modelo e sistemas corporativos.

### Deve responder
- qual sistema está sendo desenhado?
- quem interage com ele?
- que sistemas estão fora, mas conectados?
- quais limites são nativos versus integrados?

### Equivalência metodológica aproximada
Próxima do nível **system context** do C4.

## 2. Visão estrutural de contêineres conceituais
### Papel
Explicar a forma macro do sistema.

### Blocos que devem aparecer
- mission control UI
- control plane
- workflow backbone
- runtime de especialistas
- context and memory fabric
- policy and approval fabric
- observability and evidence fabric
- integration gateway

### Deve responder
- o que é centro e o que é borda?
- onde reside a semântica do sistema?
- onde a plataforma compõe capacidades de terceiros?

### Equivalência metodológica aproximada
Próxima do nível **container** do C4, mas em linguagem conceitual, não tecnológica.

## 3. Visões dinâmicas de fluxo crítico
### Papel
Explicar comportamento e transições.

### Fluxos que merecem desenho explícito
- intake de missão
- qualificação e classificação de risco
- decomposição em workflow e tasks
- execução com handoffs
- review e approval
- exceção, escalonamento e retomada
- fechamento com evidência

### Deve responder
- onde o sistema espera?
- quando humanos entram?
- quando políticas bloqueiam ou redirecionam?
- como se preserva continuidade operacional?

## 4. Visão de governança, policy e evidência
### Papel
Explicar o tecido transversal que impede a plataforma de virar apenas automação opaca.

### Deve mostrar
- pontos de enforcement de policy
- tipos de approval
- segregação de funções
- objetos de evidência
- vínculos entre decisão, estado e justificativa

### Deve responder
- quais transições críticas exigem contrapeso?
- que elementos precisam ser auditáveis?
- como autonomia varia com risco e reversibilidade?

## 5. Visão de operação humana e ownership
### Papel
Explicar como a plataforma é usada e supervisionada por pessoas reais.

### Deve mostrar
- owner da mission
- orquestrador
- especialistas
- revisores e aprovadores
- superfícies de mission control
- filas operacionais e pontos de exceção

### Deve responder
- quem decide o quê?
- quem enxerga qual estado?
- como a plataforma distribui responsabilidade?

## 6. Informações beyond views que devem atravessar tudo
### Proposta conceitual
Há informações que não pertencem a uma única visão e devem ser tratadas como camada transversal de documentação:
- glossário e termos canônicos
- atributos de qualidade e cenários
- restrições e não objetivos
- pressupostos da fase
- decisões arquiteturais
- risco e questões abertas

## Relação entre C4, arc42 e ADR neste repositório
### Proposta conceitual
- **C4** ajuda a organizar níveis de abstração para contexto e estrutura.
- **Views and Beyond** ajuda a justificar o uso de múltiplas visões e das informações transversais.
- **arc42** é útil como disciplina leve de pacote documental.
- **ADRs** preservam o porquê das escolhas, sem sobrecarregar as visões com histórico decisório.

## Recomendação prática para a próxima fase
### Recomendação
Produzir um pacote pequeno com:
1. um diagrama de contexto
2. um diagrama de contêineres conceituais
3. dois ou três diagramas dinâmicos críticos
4. uma visão explícita de governança e evidência
5. um mapa de ownership e superfícies operacionais
6. ADRs e quality scenarios como anexos vivos, não como apêndices esquecidos

## Conclusão
### Inferência
O ponto central não é escolher um framework documental “vencedor”. É garantir que a plataforma possa ser lida por diferentes públicos sem perder sua tese central: coordenação governada, backbone durável, especialistas subordinados e supervisão humana seletiva.

## Referências
- SEI, *Documenting Software Architectures: Views and Beyond, 2nd Edition*: https://www.sei.cmu.edu/library/documenting-software-architectures-views-and-beyond-second-edition/
- C4 Model: https://c4model.com/
- arc42 documentation: https://arc42.org/documentation/
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/07-mission-control-ui-and-cockpit.md`
- `docs/40-orchestration/09-orchestration-platform-conceptual-prd.md`

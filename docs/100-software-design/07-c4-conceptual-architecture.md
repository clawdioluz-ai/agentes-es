# Arquitetura conceitual em C4

## Objetivo
Traduzir a tese arquitetural do repositório em um conjunto enxuto de diagramas C4, mantendo o nível conceitual e não implementacional desta fase.

## Princípio de leitura
### Regra de escopo
Os diagramas abaixo não descrevem deployment, stack definitiva, protocolos concretos ou componentes técnicos finais. Eles documentam **estrutura conceitual, fronteiras e responsabilidades** da plataforma de orquestração governada.

### Resposta curta
A leitura C4 mais coerente para este repositório é:
1. **System context** para posicionar a plataforma no ecossistema do SDLC
2. **Container view** para mostrar o núcleo control-plane-first e suas bordas pluggable
3. **Component view** para decompor conceitualmente o control plane e o tecido de governança/evidência

## Nível 1, system context

### Pergunta que responde
Que sistema está sendo desenhado, quem interage com ele e quais sistemas externos compõem seu contexto operacional?

```mermaid
flowchart LR
    U1[Owner da missão\nproduto, engenharia ou operação]
    U2[Operador de mission control\norquestração e supervisão]
    U3[Revisor ou aprovador\nsegurança, arquitetura, delivery]

    P[Plataforma de orquestração governada\npara software delivery assistido por IA]

    S1[Sistemas de gestão do trabalho\nissues, backlog, planejamento]
    S2[Sistemas de código e entrega\ngit, PR/MR, CI/CD, testes]
    S3[Conhecimento institucional\ndocs, ADRs, runbooks, wiki]
    S4[Identidade, policy e segredos\nIAM, policy stores, secrets]
    S5[Provedores de modelo e runtimes\nLLMs e execução especializada]
    S6[Observability e incident management\ntelemetria, alertas, auditoria]

    U1 -->|solicita, enquadra e acompanha| P
    U2 -->|opera, redireciona e intervém| P
    U3 -->|revisa, aprova ou bloqueia| P

    P -->|sincroniza missão, status e artefatos| S1
    P -->|coordena mudanças e validações| S2
    P -->|recupera contexto e evidência| S3
    P -->|aplica identidade, acesso e guardrails| S4
    P -->|aciona capacidades cognitivas sob contrato| S5
    P -->|exporta e consulta sinais operacionais| S6
```

### Leitura do contexto
- a plataforma é o **sistema de interesse**
- humanos interagem com ela por papéis distintos, não por um único canal indiferenciado
- sistemas externos permanecem estruturalmente relevantes, mas fora do núcleo semântico
- provedores de modelo e runtimes entram como capacidade integrada, não como centro administrativo

## Nível 2, container view conceitual

### Pergunta que responde
Quais blocos principais compõem a plataforma e como eles cooperam para coordenar trabalho, governança e supervisão humana?

```mermaid
flowchart TB
    A[Mission control UI\nportfólio, mission detail, review, approval, cockpit]
    B[Control plane\nidentidade, estado, despacho, contratos, risco]
    C[Workflow backbone durável\nwaits, retries, branching, compensação, retomada]
    D[Runtime de especialistas\nexecução cognitiva delimitada por contrato]
    E[Context and memory fabric\nestado, working memory, retrieval, memória institucional]
    F[Policy and approval fabric\nalçadas, guardrails, segregação, checkpoints]
    G[Observability, evidence and evaluation fabric\ntraces, métricas, evidência, auditoria, avaliação]
    H[Integration gateway\ncatálogo de ferramentas e conectores do SDLC]
    X[Sistemas externos do SDLC e corporativos]

    A <--> B
    B <--> C
    C <--> D
    B <--> E
    B <--> F
    B <--> G
    D <--> H
    E <--> H
    G <--> H
    H <--> X
    F --> C
    G --> A

    classDef core fill:#eef6ff,stroke:#336699,color:#111;
    classDef cross fill:#f6f1ff,stroke:#6b46c1,color:#111;
    classDef edge fill:#eefbf3,stroke:#2f855a,color:#111;
    class A,B,C core;
    class E,F,G cross;
    class D,H,X edge;
```

### Leitura dos contêineres conceituais
- **control plane** é o centro administrativo do sistema
- **workflow backbone** sustenta durabilidade operacional e estados longos
- **runtime de especialistas** executa trabalho, mas não governa política nem estado canônico
- **policy, memory e observability** aparecem como tecidos transversais, não como apêndices
- **integration gateway** mantém a relação com o ecossistema real sem dissolver a identidade da plataforma

## Nível 3, component view conceitual do control plane

### Pergunta que responde
Que capacidades internas precisam existir no núcleo do control plane para a plataforma manter coordenação governada e auditável?

```mermaid
flowchart TB
    CP[Control plane]

    C1[Mission and workflow registry\nidentidade canônica e versionamento]
    C2[State and lifecycle coordinator\nestado agregado e transições]
    C3[Risk and autonomy classifier\ncriticidade, reversibilidade, alçada]
    C4[Contract and handoff manager\ncontratos de etapa, handoff e exceção]
    C5[Dispatch and routing orchestrator\ndespacho para backbone, especialistas e integrações]
    C6[Approval and escalation coordinator\nfilas, checkpoints, escalonamentos]
    C7[Evidence and decision ledger\njustificativas, trilha e vínculo decisório]

    CP --> C1
    CP --> C2
    CP --> C3
    CP --> C4
    CP --> C5
    CP --> C6
    CP --> C7

    C1 --> C2
    C2 --> C3
    C3 --> C4
    C4 --> C5
    C5 --> C6
    C6 --> C7
    C7 --> C2
```

### Leitura da decomposição do control plane
- o núcleo não é um bloco genérico de “coordenação”, mas um conjunto de responsabilidades discerníveis
- identidade, risco, contrato, despacho, aprovação e evidência formam uma cadeia única
- o vínculo entre **decisão** e **estado** é explícito, evitando automação opaca

## Nível 3 complementar, componentes conceituais de governança e evidência

### Pergunta que responde
Como a plataforma conecta guardrails, aprovação e explicabilidade sem reduzir isso a lógica dispersa em fluxos locais?

```mermaid
flowchart LR
    P1[Policy rules and autonomy matrix\nregras por risco, domínio e reversibilidade]
    P2[Approval policy coordinator\nquem aprova o quê e em que condição]
    P3[Segregation and access boundaries\nlimites de função, dados e ferramentas]
    P4[Evidence binder\nvínculo entre decisão, artefato e prova]
    P5[Audit and trace publisher\nexportação legível para observação e auditoria]

    IN[Solicitação de ação ou transição crítica]
    OUT[Decisão governada\nautorizada, rejeitada, escalada ou condicionada]

    IN --> P1
    P1 --> P2
    P1 --> P3
    P2 --> P4
    P3 --> P4
    P4 --> P5
    P5 --> OUT
```

### Leitura da governança transversal
- a decisão governada nasce da combinação entre **policy**, **alçada**, **acesso** e **evidência**
- aprovação não é evento isolado, mas parte de um fluxo verificável
- auditoria é consequência natural do desenho, não reconstrução posterior

## Relação entre os níveis
### Inferência
Os quatro diagramas se encadeiam assim:
- o **contexto** mostra por que a plataforma existe no ecossistema
- os **contêineres** mostram a forma macro control-plane-first
- os **componentes do control plane** mostram onde reside a semântica própria
- os **componentes de governança e evidência** mostram o tecido que impede o sistema de virar automação opaca

## Limites intencionais desta documentação
### Regra de fase
Esta documentação ainda não define:
- tecnologias mandatórias de implementação
- topologia de deployment
- contratos de API finais
- particionamento físico de serviços
- modelo definitivo de dados
- escolha final entre frameworks substituíveis de runtime, workflow ou observabilidade

## Conclusão
### Proposta conceitual
A principal contribuição do C4 nesta fase é **tornar a arquitetura legível em níveis**, preservando a tese do repositório: plataforma de orquestração governada, control-plane-first, com backbone durável, especialistas subordinados, memória governada, policy explícita e evidência de primeira classe.

## Referências
- `docs/100-software-design/02-system-context-and-boundaries.md`
- `docs/100-software-design/03-views-and-viewpoints.md`
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/06-platform-blueprint.md`
- `docs/30-framework/03-work-management-model.md`
- C4 Model: https://c4model.com/

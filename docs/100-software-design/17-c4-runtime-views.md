# Runtime views críticas da arquitetura conceitual

## Objetivo
Complementar a estrutura C4 com visões dinâmicas dos fluxos mais críticos da plataforma, mostrando como os contêineres cooperam ao longo do tempo para sustentar trabalho governado.

## Regra de leitura
As runtime views abaixo continuam conceituais. Elas mostram responsabilidades, transições e checkpoints, não protocolos finais nem chamadas de API definitivas.

## Fluxo 1, criação e qualificação de missão

### Pergunta que responde
Como uma intenção inicial vira uma mission qualificada, com identidade, risco inicial e condições mínimas para seguir?

```mermaid
sequenceDiagram
    actor Owner as Owner da missão
    participant UI as Mission control UI
    participant CP as Control plane
    participant CM as Context and memory fabric
    participant PA as Policy and approval fabric
    participant OE as Observability and evidence fabric

    Owner->>UI: descreve objetivo, contexto e restrições
    UI->>CP: mission_capture_requested
    CP->>CM: recuperar contexto institucional e histórico relevante
    CM-->>CP: contexto inicial com proveniência
    CP->>PA: avaliar criticidade, risco inicial e requisitos mínimos
    PA-->>CP: classe de risco, alçadas e checkpoints iniciais
    CP->>CP: criar mission, registrar owner e critérios iniciais
    CP-->>UI: mission_captured / mission_qualified
    CP->>OE: publicar trilha de decisão e evidência de intake
    OE-->>UI: timeline e status atualizados
```

### Leitura do fluxo
- a UI capta intenção, mas a criação formal ocorre no control plane
- contexto e policy entram cedo para evitar intake cego
- a qualificação já produz trilha auditável, não apenas abertura informal

## Fluxo 2, decomposição governada da missão

### Pergunta que responde
Como uma mission qualificada é convertida em workflow, tasks, dependências e checkpoints sem perder rastreabilidade?

```mermaid
sequenceDiagram
    participant CP as Control plane
    participant CM as Context and memory fabric
    participant RT as Runtime de especialistas
    participant PA as Policy and approval fabric
    participant OE as Observability and evidence fabric
    participant UI as Mission control UI

    CP->>CM: solicitar contexto ampliado e artefatos relevantes
    CM-->>CP: contexto preparado para planejamento
    CP->>RT: solicitar proposta de decomposição sob contrato
    RT-->>CP: proposta de workflow, tasks, handoffs e lacunas
    CP->>PA: validar autonomia, separação de funções e checkpoints obrigatórios
    PA-->>CP: restrições, approvals requeridos e limites de execução
    CP->>CP: consolidar workflow versionado e tasks canônicas
    CP->>OE: registrar justificativa, proposta aceita e riscos residuais
    CP-->>UI: mission_decomposed com plano observável
```

### Leitura do fluxo
- especialistas podem propor decomposição, mas não a canonizam sozinhos
- policy atua sobre o plano antes da execução, não apenas depois do risco materializado
- a decomposição precisa produzir rastreabilidade entre objetivo superior e cada task

## Fluxo 3, delegação de task para especialista

### Pergunta que responde
Como uma task pronta é delegada com contexto suficiente, limites claros e retorno estruturado?

```mermaid
sequenceDiagram
    participant CP as Control plane
    participant WB as Workflow backbone
    participant CM as Context and memory fabric
    participant RT as Runtime de especialistas
    participant IG as Integration gateway
    participant OE as Observability and evidence fabric

    CP->>WB: workflow_start_or_continue com próxima task elegível
    WB->>CM: solicitar task_context_prepared
    CM-->>WB: pacote de contexto com proveniência e restrições
    WB->>RT: task_assigned com contrato, contexto e limites
    RT->>IG: acessar ferramentas autorizadas quando necessário
    IG-->>RT: dados externos ou confirmação de ação permitida
    RT-->>WB: specialist_output_submitted / specialist_blocked
    WB-->>CP: workflow_progressed com resultado da task
    CP->>OE: registrar execução, uso de ferramentas e evidência produzida
```

### Leitura do fluxo
- o backbone coordena a execução durável, mas o control plane continua lendo o resultado em termos de domínio
- contexto chega preparado e governado, em vez de acesso livre a tudo
- ações externas passam pelo integration gateway, não diretamente pelo especialista

## Fluxo 4, review de saída relevante

### Pergunta que responde
Como uma entrega produzida vira objeto formal de review e retorna para retrabalho ou segue adiante?

```mermaid
sequenceDiagram
    participant RT as Runtime de especialistas
    participant WB as Workflow backbone
    participant CP as Control plane
    participant OE as Observability and evidence fabric
    participant UI as Mission control UI
    actor Reviewer as Revisor

    RT-->>WB: specialist_output_submitted com evidência inicial
    WB-->>CP: workflow_progressed / task_output_available
    CP->>OE: consolidar evidence pack para review
    OE-->>CP: evidence_pack_ready
    CP-->>UI: review_requested
    Reviewer->>UI: analisa artefatos, evidência e critérios
    UI->>CP: review_decision_submitted
    alt review aceito
        CP->>CP: marcar task em handoff_pending ou awaiting_approval
    else review rejeitado
        CP->>WB: solicitar retrabalho / retomada da task
    end
    CP->>OE: registrar decisão de review e justificativa
```

### Leitura do fluxo
- review é ato formal sustentado por evidence pack, não simples comentário difuso
- o resultado do review pode gerar retrabalho ou avançar a missão
- a decisão fica vinculada à trilha observável da tarefa e da missão

## Fluxo 5, approval de ação crítica

### Pergunta que responde
Como a plataforma segura uma transição crítica até que a alçada correta autorize o avanço?

```mermaid
sequenceDiagram
    participant CP as Control plane
    participant PA as Policy and approval fabric
    participant OE as Observability and evidence fabric
    participant UI as Mission control UI
    participant WB as Workflow backbone
    actor Approver as Aprovador

    CP->>PA: avaliar transição crítica e approval requerido
    PA-->>CP: tipo de approval, alçada e condições
    CP->>OE: consolidar impacto, reversibilidade, evidência e tradeoffs
    CP-->>UI: approval_requested
    Approver->>UI: revisa pedido e evidências
    UI->>CP: approval_decision_submitted
    CP->>PA: registrar decisão e validar condições finais
    PA-->>CP: approval_decision_recorded ou bloqueio
    alt aprovado
        CP->>WB: workflow_resume_requested ou transição terminal
    else rejeitado ou condicionado
        CP->>WB: manter pausa ou redirecionar para ajustes
    end
    CP->>OE: publicar decisão, justificativa e impacto
```

### Leitura do fluxo
- approval difere de review porque autoriza a transição, não apenas avalia a qualidade
- policy define a alçada e as condições, mas a autorização material é registrada no fluxo
- o workflow backbone só retoma quando a decisão governada estiver registrada

## Fluxo 6, conclusão e fechamento da missão

### Pergunta que responde
Como a missão chega ao estado de concluída com artefatos finais, evidência, pendências e aprendizado explícitos?

```mermaid
sequenceDiagram
    participant WB as Workflow backbone
    participant CP as Control plane
    participant OE as Observability and evidence fabric
    participant IG as Integration gateway
    participant UI as Mission control UI
    participant CM as Context and memory fabric

    WB-->>CP: workflow_completed
    CP->>OE: consolidar resultado, evidência final, métricas e decisões tomadas
    OE-->>CP: pacote final de conclusão e trilha de auditoria
    CP->>IG: sincronizar status e artefatos finais com sistemas externos relevantes
    IG-->>CP: confirmações e vínculos externos
    CP->>CM: registrar memória institucional útil e lições aprendidas selecionadas
    CP-->>UI: mission_completed ou closed_with_constraints
    CP->>OE: publicar fechamento e restrições remanescentes
```

### Leitura do fluxo
- concluir não é apenas terminar execução, mas consolidar resultado verificável
- integração externa e memória institucional entram no encerramento, não só na execução
- o fechamento pode manter restrições explícitas, preservando honestidade operacional

## Síntese das runtime views
As seis visões acima mostram a arquitetura em movimento:
- **criação** transforma intenção em objeto governado
- **decomposição** converte objetivo em plano versionado
- **delegação** aciona especialistas sob contrato e contexto preparado
- **review** compara saída e contrato com evidência acessível
- **approval** controla transições críticas por alçada e risco
- **conclusão** fecha a missão com trilha, sincronização externa e aprendizado

## Relação com o restante da seção
Estas runtime views complementam:
- `05-conceptual-domain-model.md`, ao colocar mission, workflow e task em movimento
- `07-c4-conceptual-architecture.md`, ao sair da estrutura estática para o comportamento
- `08-c4-container-index.md` a `16-c4-container-integration-gateway.md`, ao mostrar cooperação entre contêineres

## Conclusão
A arquitetura C4 do repositório deixa de ser apenas uma fotografia estrutural e passa a incluir os fluxos que mais importam para uma plataforma de orquestração governada: intake, decomposição, delegação, review, approval e completion.

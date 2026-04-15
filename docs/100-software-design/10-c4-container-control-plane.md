# Contêiner, control plane

## Objetivo
Detalhar o núcleo administrativo e semântico da plataforma, responsável por identidade do trabalho, coordenação, risco, despacho, governança operacional e trilha decisória.

## Responsabilidades
- manter o sistema de registro de mission, workflow, task, review, approval, handoff, artifact e evidence
- coordenar ciclos de vida, transições e consistência semântica
- classificar risco, criticidade, reversibilidade e autonomia permitida
- despachar execução para workflow backbone, runtime de especialistas e integrações
- registrar decisões, justificativas, exceções e vínculos com evidência
- acionar checkpoints humanos e escalonamentos quando necessário

## O que está dentro da fronteira
- registry canônico de objetos de trabalho
- coordenador de estado e lifecycle
- classificador de risco e autonomia
- gerenciador de contratos e handoffs
- orquestrador de despacho e roteamento
- coordenador de approvals e escalonamentos
- ledger de decisão e evidência vinculada

## O que está fora da fronteira
- renderização de interface e interação de apresentação
- execução longa de waits e retries como preocupação primária
- raciocínio especializado e uso direto de ferramentas no detalhe operacional
- armazenamento especializado de logs brutos e traces de alto volume

## Entradas
- comandos humanos vindos da mission control UI ou APIs
- eventos do workflow backbone sobre progresso, falhas, pausas e retomadas
- saídas estruturadas do runtime de especialistas
- resultados de policy, approvals, observabilidade e integrações externas

## Saídas
- ordens de criação, atualização, pausa, retomada ou compensação de workflows
- contratos de task, handoff e solicitação de execução a especialistas
- pedidos de review, approval e escalonamento
- eventos de domínio para observabilidade, UI e integrações

## Dados possuídos
- identidade e versão de mission, workflow e task
- estado agregado e local
- matrizes de relacionamento entre objetivo, task, artefatos e evidências
- histórico decisório, ownership, alçadas aplicadas e exceções registradas

## Dados apenas referenciados
- documentos, código, pipelines e outros artefatos externos ao núcleo
- traces de baixo nível, logs extensos e datasets de avaliação
- secrets e políticas detalhadas mantidas em fabric especializado

## Eventos consumidos
- `mission_capture_requested`
- `workflow_progressed`
- `workflow_waiting`
- `specialist_output_submitted`
- `review_decision_submitted`
- `approval_decision_submitted`
- `policy_violation_detected`
- `external_signal_received`

## Eventos emitidos
- `mission_captured`
- `mission_qualified`
- `mission_decomposed`
- `task_created`
- `task_assigned`
- `task_blocked`
- `review_requested`
- `approval_requested`
- `mission_escalated`
- `mission_completed`

## Integrações
- workflow backbone para execução durável
- policy and approval fabric para decisão governada
- context and memory fabric para recuperação contextual e proveniência
- observability fabric para publicação de eventos, métricas e evidências
- integration gateway para refletir trabalho em sistemas externos

## Dependências conceituais
- modelo canônico de trabalho aceito por produto, operação e arquitetura
- taxonomia de eventos e transições estável
- contratos explícitos para tasks, reviews, approvals, handoffs e exceções

## Restrições e constraints
- não pode delegar a lógica semântica central ao runtime de especialistas
- deve preservar separação entre decisão, execução e aprovação
- precisa suportar replanejamento e versionamento sem perder rastreabilidade
- deve operar como fonte canônica mesmo com múltiplos canais de entrada

## Observabilidade esperada
- tempo de ciclo por mission, workflow e task
- taxa de replanejamento e retrabalho por classe de missão
- incidência de bloqueios, escalonamentos e policy mismatches
- latência de decisão entre checkpoint crítico e despacho seguinte
- cobertura de evidência em transições materiais

## Riscos principais
- virar um hub centralizado demais, com excesso de responsabilidade e baixa evolutividade
- misturar estado canônico com detalhes transitórios de execução
- permitir que exceções bypassem o modelo sem registro suficiente

## Decisões em aberto
- qual granularidade de versionamento é necessária para workflow e task?
- até onde o control plane recalcula plano versus apenas aceita propostas de decomposição?
- como particionar o ledger decisório sem perder legibilidade do histórico?

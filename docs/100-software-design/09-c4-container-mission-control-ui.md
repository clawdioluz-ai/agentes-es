# Contêiner, mission control UI

## Objetivo
Definir a fronteira conceitual da interface operacional da plataforma, responsável por intake, acompanhamento, revisão, aprovação e intervenção humana.

## Responsabilidades
- receber missões por superfícies de entrada governadas
- exibir portfólio, mission detail, filas de review e approval, bloqueios e escalonamentos
- permitir intervenção humana estruturada, não apenas conversacional
- transformar ações humanas em comandos explícitos para o control plane
- tornar risco, evidência, aging e dependências legíveis

## O que está dentro da fronteira
- inbox e intake de missão
- portfólio de missões e cockpit operacional
- mission detail com workflow, tasks, handoffs, artifacts e evidence
- review queue e approval center
- superfícies de comentário, instrução, exceção e escalonamento

## O que está fora da fronteira
- estado canônico de missão, workflow e task
- lógica de risco, política e alçadas
- execução durável de fluxo
- execução cognitiva de especialistas
- conectores técnicos com sistemas externos

## Entradas
- comandos humanos, como criar missão, aprovar, rejeitar, replanejar, bloquear ou encerrar
- eventos de atualização de estado vindos do control plane e do fabric de observabilidade
- contexto recuperado para exibição, comparação e decisão

## Saídas
- comandos estruturados ao control plane
- pedidos de review, approval, rework ou escalonamento
- sinais de interação humana relevantes para auditoria e experiência operacional

## Dados possuídos
- preferências locais de apresentação, filtros e ordenação
- drafts temporários de interação antes de submissão

## Dados apenas referenciados
- mission, workflow, task, review, approval, handoff, artifact e evidence
- métricas, traces, custos, risco e policy aplicável

## Eventos consumidos
- `mission_captured`
- `mission_state_changed`
- `task_assigned`
- `task_blocked`
- `review_requested`
- `approval_requested`
- `escalation_opened`
- `mission_completed`

## Eventos emitidos
- `mission_capture_requested`
- `mission_replan_requested`
- `review_decision_submitted`
- `approval_decision_submitted`
- `manual_override_requested`
- `escalation_comment_added`

## Integrações
- control plane para comandos e leitura do modelo canônico
- observability fabric para timeline, métricas e trilhas legíveis
- context and memory fabric para recuperar contexto, referências e evidências relevantes
- canais de entrada e notificação, como chat, e-mail, issue, PR ou APIs de produto

## Dependências conceituais
- contrato claro entre ação de interface e comando de domínio
- taxonomia de estados e filas operacionais estável
- vínculo entre UI e evidência auditável, evitando ações invisíveis

## Restrições e constraints
- não pode concentrar lógica decisória crítica que só exista na interface
- deve funcionar com múltiplas superfícies de entrada sem mudar o núcleo semântico
- precisa representar incerteza, risco e pendência sem fingir completude

## Observabilidade esperada
- tempo entre pedido humano e efetivação do comando
- aging de reviews e approvals na fila
- taxa de ações humanas sem evidência suficiente
- taxa de reversão de decisões tomadas via UI
- pontos de abandono, retrabalho e confusão operacional

## Riscos principais
- virar front-end rico sobre um backend sem semântica estável
- esconder decisões críticas em chat, comentários ou widgets dispersos
- induzir automação excessiva por UX que omite risco e reversibilidade

## Decisões em aberto
- qual combinação de superfícies será primária no primeiro incremento, chat, web app ou ambas?
- que parte da experiência deve ser síncrona versus assíncrona?
- como representar exceções e overrides sem normalizá-los como caminho feliz?

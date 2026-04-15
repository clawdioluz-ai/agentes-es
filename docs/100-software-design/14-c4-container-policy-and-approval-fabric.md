# Contêiner, policy and approval fabric

## Objetivo
Tornar explícita a camada transversal que governa autonomia, acesso, alçadas, segregação de funções, checkpoints humanos e tratamento de exceções.

## Responsabilidades
- avaliar risco, reversibilidade e criticidade contra políticas aplicáveis
- determinar quando review, approval, escalonamento ou bloqueio são obrigatórios
- impor segregação entre criação, execução, revisão e autorização
- registrar justificativas, exceções e condições de liberação

## O que está dentro da fronteira
- matriz de autonomia por classe de risco
- regras de approval e alçada
- políticas de segregação de funções e boundaries de acesso
- avaliação de exceção e override governado

## O que está fora da fronteira
- experiência de interface para tomada de decisão
- execução operacional do workflow
- storage primário de missões e tasks como autoridade de domínio
- gestão detalhada de telemetria bruta

## Entradas
- pedidos do control plane para avaliar uma ação, transição ou plano
- contexto de risco, evidência disponível e reversibilidade
- decisões humanas submetidas pela UI
- sinais externos de conformidade, segurança ou compliance

## Saídas
- decisões como permitir, negar, condicionar, revisar, escalar ou bloquear
- requisitos de evidência e de aprovador por classe de decisão
- registros de exceção, override e justificativa

## Dados possuídos
- regras e matrizes de autonomia, alçadas e segregação
- histórico de decisões de policy e exceções
- catálogos de tipos de approval e condições de liberação

## Dados apenas referenciados
- evidências, artefatos e estados do control plane
- identidades, grupos e segredos mantidos em sistemas corporativos
- logs detalhados de observabilidade e execução

## Eventos consumidos
- `risk_evaluation_requested`
- `approval_requested`
- `review_decision_submitted`
- `approval_decision_submitted`
- `external_compliance_signal_received`

## Eventos emitidos
- `risk_evaluated`
- `policy_violation_detected`
- `approval_requirement_defined`
- `approval_decision_recorded`
- `override_registered`
- `segregation_conflict_detected`

## Integrações
- control plane como principal consumidor e coordenador
- mission control UI para decisões humanas e explicações operacionais
- context and memory fabric para contexto normativo e documental
- identity, policy stores e secrets externos, via integration gateway
- observability fabric para trilha auditável e métricas de governança

## Dependências conceituais
- taxonomia de risco e reversibilidade coerente com o domínio
- separação explícita entre review e approval
- vínculo obrigatório entre decisão material e evidência acessível

## Restrições e constraints
- políticas não podem viver apenas em prompts, playbooks locais ou convenções tácitas
- exceções precisam ser raras, justificadas e rastreáveis
- deve sustentar mudança incremental de política sem quebrar rastreabilidade histórica

## Observabilidade esperada
- volume e aging de approvals por tipo
- taxa de bloqueio, override e exceção
- cobertura de segregação de funções em ações críticas
- tempos de resposta de approval e gargalos de alçada
- proporção de decisões críticas com evidência insuficiente

## Riscos principais
- fricção operacional excessiva se tudo exigir approval humano
- normalização de overrides até virarem caminho padrão
- desalinhamento entre policy declarada e prática real do fluxo

## Decisões em aberto
- que modelo melhor representa a matriz de autonomia, regras fixas, políticas declarativas ou abordagem híbrida?
- como versionar policy aplicada para auditoria de decisões passadas?
- qual limiar de risco deve disparar dupla aprovação ou segregação reforçada?

# Contêiner, workflow backbone durável

## Objetivo
Definir a camada responsável por executar trabalho de longa duração com confiabilidade, pausas, retomadas e coordenação temporal fora da memória efêmera de agentes.

## Responsabilidades
- persistir execução de workflows e seus checkpoints
- suportar waits, retries, timers, joins, branching e compensações
- pausar fluxos para review, approval, dependências externas ou intervenção humana
- retomar trabalho após eventos externos, falhas ou janelas longas
- devolver ao control plane progresso operacional consistente

## O que está dentro da fronteira
- runtime de execução durável de workflows
- mecanismos de timer, espera e retomada
- coordenação de paralelismo e sincronização
- tratamento de falha operacional, retry e compensação

## O que está fora da fronteira
- semântica de negócio e estado canônico do domínio
- decisão final de risco, approval ou exceção
- especialização cognitiva de tarefas
- experiência de usuário e gestão visual do portfólio

## Entradas
- ordens do control plane para iniciar, pausar, retomar, cancelar, compensar ou replanejar um workflow
- sinais externos encaminhados pelo control plane ou integration gateway
- respostas de especialistas, revisores, aprovadores e serviços externos

## Saídas
- eventos de progresso, espera, timeout, falha, retry, compensação e conclusão
- pedidos operacionais de execução de task para o runtime de especialistas
- notificações de bloqueio quando dependências não se resolvem

## Dados possuídos
- estado operacional de execução do workflow
- checkpoints, timers, contadores de retry e correlação de espera
- histórico técnico de retomada e compensação

## Dados apenas referenciados
- definição canônica da mission e do workflow no control plane
- evidência de negócio e artefatos finais
- políticas, alçadas e regras de risco

## Eventos consumidos
- `workflow_start_requested`
- `workflow_pause_requested`
- `workflow_resume_requested`
- `workflow_cancel_requested`
- `external_signal_received`
- `specialist_output_submitted`
- `approval_decision_recorded`

## Eventos emitidos
- `workflow_started`
- `workflow_progressed`
- `workflow_waiting`
- `workflow_retry_scheduled`
- `workflow_timed_out`
- `workflow_compensation_started`
- `workflow_failed`
- `workflow_completed`

## Integrações
- control plane como cliente primário e consumidor do progresso
- runtime de especialistas para execução das unidades de trabalho
- integration gateway para escutar ou disparar sinais dependentes do SDLC
- observability fabric para traces, métricas de duração e falhas

## Dependências conceituais
- contratos claros de entrada e saída de task
- correlação robusta entre eventos operacionais e objetos de domínio
- mecanismo explícito para pauses humanas, não apenas sleeps técnicos

## Restrições e constraints
- não deve se tornar a fonte de verdade semântica da plataforma
- precisa lidar com execuções longas, incompletas e reentrantes
- deve tolerar falhas parciais sem perder correlacionamento com missão

## Observabilidade esperada
- duração por workflow e por etapa
- filas de espera e causas de pausa
- taxa de retry, timeout e compensação
- work in progress parado por falta de sinal externo
- discrepância entre progresso operacional e leitura de negócio

## Riscos principais
- vazar semântica de negócio para a engine de workflow
- modelar fluxos rígidos demais, dificultando replanejamento
- mascarar falhas estruturais com retries excessivos

## Decisões em aberto
- quão declarativa versus programática deve ser a definição futura de workflow?
- que tipo de compensação é obrigatória por classe de ação?
- como tratar mudanças materiais de plano em workflows já em curso?

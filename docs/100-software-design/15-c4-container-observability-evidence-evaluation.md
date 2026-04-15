# Contêiner, observability, evidence and evaluation fabric

## Objetivo
Definir o tecido que explica o comportamento da plataforma, conecta execução a evidência verificável e permite medir qualidade operacional e decisória.

## Responsabilidades
- coletar traces, métricas, custos, eventos e sinais operacionais da plataforma
- organizar evidência vinculada a decisões, transições e artefatos materiais
- publicar timelines legíveis para operação, auditoria e aprendizagem
- sustentar avaliação online e offline de qualidade, segurança e efetividade

## O que está dentro da fronteira
- tracing fim a fim por missão, workflow, task, especialista e ferramenta
- ledger observável de eventos e correlações
- catálogo de evidências e vínculos com decisões materiais
- mecanismos de avaliação e comparação de resultados

## O que está fora da fronteira
- decisão semântica primária sobre estado do domínio
- execução do workflow ou do especialista
- ownership do artefato externo original
- política decisória como autoridade final

## Entradas
- eventos emitidos por control plane, workflow backbone, runtime e integration gateway
- decisões de review, approval, exceção e conclusão
- sinais de qualidade vindos de testes, pipelines, revisões e avaliações

## Saídas
- timelines operacionais e de auditoria
- indicadores de qualidade, custo, throughput, aging e retrabalho
- pacotes de evidência para review e approval
- insumos para melhoria contínua de política, fluxo e especialização

## Dados possuídos
- traces, métricas agregadas, correlações e indicadores
- vínculos entre decisão, evidência, artefato e evento
- resultados de avaliação comparativa e histórico analítico

## Dados apenas referenciados
- artefatos originais em sistemas externos
- estados canônicos do domínio mantidos no control plane
- regras de policy e identidades corporativas

## Eventos consumidos
- praticamente todos os eventos relevantes de domínio e operação, com destaque para `task_assigned`, `tool_invoked`, `review_requested`, `approval_decision_recorded`, `workflow_failed`, `mission_completed`

## Eventos emitidos
- `evidence_pack_ready`
- `operational_anomaly_detected`
- `quality_regression_detected`
- `audit_export_requested`
- `evaluation_completed`

## Integrações
- todos os contêineres internos como produtores de sinal
- mission control UI para visualização operacional
- integration gateway para importar sinais de CI, code review, incidentes e outros sistemas
- eventuais stacks de tracing, logging, métricas e evaluation, mantendo plugabilidade

## Dependências conceituais
- IDs correlacionáveis entre missão, workflow, task, tool call, review e approval
- modelo claro do que conta como evidência versus mero log
- critérios de qualidade e sucesso por classe de missão

## Restrições e constraints
- não deve depender exclusivamente de reconstrução manual posterior
- precisa tornar visível tanto performance quanto governança
- deve equilibrar retenção, custo e utilidade analítica

## Observabilidade esperada
- este contêiner é o próprio local da capacidade observável, portanto deve expor cobertura, atraso de ingestão, lacunas de correlação e qualidade dos vínculos de evidência
- também deve permitir leitura de custo, latência, falhas, retrabalho, aprovação, aging, risco residual e resultado entregue

## Riscos principais
- capturar muito sinal sem modelo analítico útil
- chamar qualquer log de evidência, enfraquecendo review e approval
- gerar dependência excessiva de uma stack de observabilidade específica

## Decisões em aberto
- que subconjunto mínimo de eventos precisa ser obrigatório desde a fase 1?
- como ligar evidência humana, como comentários e sign-offs, a traces automatizados?
- qual estratégia de avaliação permite comparar especialistas, fluxos e políticas sem cair em métricas vaidosas?

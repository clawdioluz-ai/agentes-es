# Contêiner, runtime de especialistas

## Objetivo
Descrever o contêiner que executa trabalho cognitivo e operacional especializado sob contrato, sem assumir o papel de governança central da plataforma.

## Responsabilidades
- executar tasks delimitadas por objetivo, entradas, saídas esperadas e limites de autonomia
- selecionar ou acionar especialistas, skills e ferramentas autorizadas
- produzir saídas estruturadas com confiança, lacunas e necessidade de escalonamento
- respeitar contratos de handoff, contexto e uso de ferramentas

## O que está dentro da fronteira
- execução de especialistas automatizados ou semiautomatizados
- seleção de skill ou perfil especializado
- acesso mediado a ferramentas autorizadas
- geração de saída estruturada e metadados de confiança

## O que está fora da fronteira
- decisão canônica sobre risco, approval e estado agregado
- registro mestre de missão e task
- política corporativa e gerenciamento de segredos como autoridade final
- armazenamento institucional de evidência e observabilidade como fonte de verdade

## Entradas
- contratos de task emitidos pelo control plane ou workflow backbone
- contexto autorizado vindo do context and memory fabric
- capacidades e conectores expostos via integration gateway

## Saídas
- resultado da task
- declaração de confiança, limitações e evidência produzida
- pedidos de clarificação, bloqueio, replanejamento ou escalonamento
- eventos de uso de ferramenta e progresso material

## Dados possuídos
- estado efêmero de execução da task
- working memory local e transitória
- logs operacionais específicos da sessão de execução

## Dados apenas referenciados
- missão, workflow, task e policy aplicável
- documentos, código, backlog, pipelines e conhecimento recuperado
- históricos institucionais usados apenas como contexto

## Eventos consumidos
- `task_assigned`
- `task_context_prepared`
- `tool_access_granted`
- `task_rework_requested`
- `task_cancel_requested`

## Eventos emitidos
- `specialist_started`
- `tool_invoked`
- `specialist_output_submitted`
- `specialist_low_confidence_reported`
- `specialist_blocked`
- `specialist_escalation_requested`

## Integrações
- control plane e workflow backbone para contratos e retorno estruturado
- context and memory fabric para contexto operacional e conhecimento
- integration gateway para ferramentas do SDLC e sistemas corporativos
- observability fabric para tracing, custos e qualidade observada

## Dependências conceituais
- contratos de task suficientemente explícitos
- catálogo de capacidades e limites por especialista
- boundaries claros entre ferramenta autorizada, contexto permitido e ação proibida

## Restrições e constraints
- não pode assumir acesso irrestrito ao ecossistema externo
- deve declarar incerteza e lacunas, não ocultá-las
- precisa aceitar interrupção, revisão e reexecução parcial
- deve ser substituível sem romper o modelo do control plane

## Observabilidade esperada
- taxa de sucesso por tipo de task e especialista
- custo, latência e consumo de modelo por classe de missão
- frequência de bloqueio por falta de contexto ou ferramenta
- taxa de baixa confiança, escalonamento e retrabalho
- correlação entre especialista usado e qualidade posterior da saída

## Riscos principais
- concentração excessiva de inteligência implícita fora do modelo governado
- dependência de um único runtime ou fornecedor de modelo
- resultados persuasivos, porém pouco verificáveis

## Decisões em aberto
- como classificar especialistas por domínio, criticidade e autonomia?
- até que ponto o runtime pode propor decomposição ou apenas executar tasks?
- qual nível de padronização a saída estruturada deve exigir entre especialistas heterogêneos?

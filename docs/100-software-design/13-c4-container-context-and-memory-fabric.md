# Contêiner, context and memory fabric

## Objetivo
Especificar o tecido de contexto e memória que abastece a plataforma com informação útil, governada por escopo, proveniência, sensibilidade e retenção.

## Responsabilidades
- separar contexto operacional, memória de trabalho, conhecimento recuperável e memória institucional
- preparar contexto mínimo suficiente para missão, workflow, task, review e approval
- registrar proveniência, frescor, sensibilidade e escopo de uso
- reduzir ambiguidade e repetição de coleta manual de contexto

## O que está dentro da fronteira
- preparação de contexto operacional por objeto de domínio
- retrieval de conhecimento e documentos relevantes
- indexação conceitual de fontes institucionais
- metadados de proveniência, retenção e sensibilidade

## O que está fora da fronteira
- estado canônico do trabalho como fonte de verdade primária
- execução de tarefas especializadas
- política decisória final sobre autorização ou approval
- ownership dos sistemas originais de documentação e código

## Entradas
- consultas do control plane, UI, runtime de especialistas e observability fabric
- documentos, artefatos e sinais vindos pelo integration gateway
- eventos de missão e task que mudam a necessidade contextual

## Saídas
- pacotes de contexto preparados por missão ou task
- referências recuperadas com proveniência explícita
- avisos de contexto insuficiente, inconsistente ou sensível

## Dados possuídos
- índices, embeddings, catálogos e metadados de proveniência
- working sets contextuais preparados para execuções específicas
- políticas de retenção e classificação contextual derivadas

## Dados apenas referenciados
- conteúdo original em docs, wikis, repositórios, tickets e sistemas externos
- segredos, dados regulados ou material sensível sob autoridade de outros sistemas

## Eventos consumidos
- `mission_captured`
- `mission_decomposed`
- `task_created`
- `task_context_requested`
- `artifact_linked`
- `knowledge_source_updated`

## Eventos emitidos
- `task_context_prepared`
- `context_gap_detected`
- `sensitive_context_flagged`
- `knowledge_refresh_completed`

## Integrações
- integration gateway para acesso a fontes externas
- control plane para associar contexto ao domínio de trabalho
- runtime de especialistas e UI como consumidores de contexto preparado
- policy fabric para restrições de acesso e classificação

## Dependências conceituais
- taxonomia clara de tipos de memória e contexto
- contratos de proveniência e classificação de sensibilidade
- mecanismos de atualização e expiração compatíveis com o fluxo de trabalho

## Restrições e constraints
- não deve virar um lago de contexto amorfo sem governança
- precisa distinguir referência recuperada de evidência válida para decisão
- deve minimizar excesso de contexto que degrade foco, custo e explicabilidade

## Observabilidade esperada
- cobertura contextual por tipo de task
- taxa de recuperação útil versus ruído
- incidência de contexto desatualizado ou inconsistente
- uso de fontes sensíveis e pedidos negados por política
- impacto do contexto na taxa de sucesso e retrabalho

## Riscos principais
- confundir memória institucional com estado operacional vivo
- promover contexto recuperado a “verdade” sem validação
- ampliar superfície de exposição de dados sensíveis

## Decisões em aberto
- qual estratégia de retenção deve diferenciar working memory, memória institucional e evidência?
- que critérios tornam uma referência recuperada apta a sustentar decisão material?
- como versionar contexto preparado quando a missão muda de escopo?

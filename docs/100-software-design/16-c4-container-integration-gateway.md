# Contêiner, integration gateway

## Objetivo
Documentar a borda controlada entre a plataforma e o ecossistema do SDLC e sistemas corporativos, preservando contratos, autorização e semântica de plataforma.

## Responsabilidades
- expor catálogo governado de ferramentas, conectores e capacidades externas
- traduzir chamadas da plataforma para APIs, eventos e superfícies externas
- aplicar autenticação, autorização e limites por ferramenta, contexto e etapa
- normalizar retorno externo para contratos utilizáveis pelo control plane e runtime

## O que está dentro da fronteira
- catálogo de integrações e ferramentas autorizadas
- adaptadores para git, backlog, CI/CD, docs, identidade, incidentes, observabilidade e canais externos
- camada de mediação de acesso e contrato
- mecanismos de rate limit, erro, idempotência e correlação externa

## O que está fora da fronteira
- lógica de negócio da missão
- decisão de risco e approval
- UI e experiência operacional
- ownership dos sistemas externos integrados

## Entradas
- pedidos de leitura, escrita, consulta ou ação vindos do control plane, runtime, context fabric ou observability fabric
- eventos e webhooks de sistemas externos

## Saídas
- respostas normalizadas, artefatos recuperados e confirmações de ação externa
- sinais externos correlacionados para o workflow backbone e control plane
- erros de integração, limitação, autorização ou inconsistência

## Dados possuídos
- catálogo de conectores, contratos e metadados operacionais de integração
- correlações externas, status transitório de chamadas e políticas de acesso por ferramenta

## Dados apenas referenciados
- código, tickets, documentos, pipelines, identidades e incidentes em sistemas externos
- segredos sob autoridade de cofres ou provedores especializados

## Eventos consumidos
- `tool_access_requested`
- `artifact_fetch_requested`
- `external_write_requested`
- `webhook_received`

## Eventos emitidos
- `tool_access_granted`
- `external_signal_received`
- `artifact_linked`
- `integration_failure_detected`
- `rate_limit_encountered`

## Integrações
- sistemas de gestão de trabalho, repositórios, code review, CI/CD, documentação, IAM, secrets, incident tools, observability stacks e canais de comunicação
- todos os demais contêineres internos como consumidores indiretos

## Dependências conceituais
- contratos de ferramenta estáveis e auditáveis
- boundaries claros entre ação permitida, ação proibida e ação condicionada
- correlação robusta entre chamada externa e objeto de domínio interno

## Restrições e constraints
- integrações não podem carregar sozinhas a semântica do fluxo
- precisa suportar plugabilidade sem reescrever o domínio
- deve tratar escrita externa como ação material sujeita a policy, evidência e reversibilidade

## Observabilidade esperada
- latência e taxa de erro por conector
- incidência de rate limit, negação de acesso e inconsistência externa
- volume de ações de escrita por tipo de sistema e classe de risco
- tempo entre sinal externo e retomada do workflow correspondente

## Riscos principais
- proliferação de conectores ad hoc com contratos frágeis
- efeitos colaterais externos sem evidência ou correlação suficiente
- lock-in criado por adaptadores altamente específicos

## Decisões em aberto
- qual subconjunto de integrações deve ser tratado como plataforma nativa no início?
- como padronizar contratos sem achatar diferenças materiais entre sistemas externos?
- que política de escrita externa deve ser obrigatoriamente idempotente ou reversível?

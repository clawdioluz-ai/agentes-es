# Roadmap de maturidade

## Objetivo
Traduzir a tese do repositório em uma sequência de evolução organizacional e arquitetural. O propósito aqui não é estimar implementação, mas deixar claro quais capacidades aparecem em cada nível, quais riscos predominam e qual evidência mínima deveria existir antes de avançar.

## Como ler este documento
- **Nível** indica um estágio de maturidade observável.
- **Capacidades típicas** descrevem o que passa a existir naquele estágio.
- **Riscos dominantes** mostram onde a adoção costuma falhar.
- **Critério de passagem** indica o que precisa estar razoavelmente demonstrado antes de subir de nível.

## Visão resumida

| Nível | Descrição curta | Centro de gravidade | Risco dominante |
|---|---|---|---|
| 1 | assistência localizada | produtividade individual | confundir uso pontual com transformação sistêmica |
| 2 | workflows assistidos | padronização por etapa | automação fragmentada e sem governança comum |
| 3 | orquestração parcial | handoffs explícitos | fronteiras borradas entre especialistas e coordenação |
| 4 | orquestração ponta a ponta governada | control plane, policy e evidência | escalar autonomia sem medição e alçadas maduras |
| 5 | plataforma adaptativa | aprendizado governado | aumentar autonomia acima da capacidade de controle |

## Nível 1. Assistência localizada
### Descrição
Copilots e suporte pontual ao desenvolvedor.

### Capacidades típicas
- apoio à escrita de código, testes, documentação ou consulta técnica
- uso individual ou por pequenos grupos
- contexto ainda concentrado em editor, chat ou tarefa imediata
- pouca integração com handoffs formais do SDLC

### Sinais positivos
- ganhos locais de velocidade percebida
- adoção voluntária em tarefas delimitadas
- primeiros padrões de uso preferencial por tipo de atividade

### Riscos dominantes
- medir apenas satisfação ou velocidade subjetiva
- ausência de política mínima para dados, código e review
- criação de dependência operacional sem rastreabilidade suficiente

### Critério de passagem
### Inferência
Só vale avançar quando a organização consegue provar que o uso pontual gera valor recorrente e já possui pelo menos controles mínimos de segurança, revisão e contexto de uso.

## Nível 2. Workflows assistidos
### Descrição
IA apoia etapas específicas com templates, validações e artefatos padronizados.

### Capacidades típicas
- apoio estruturado a requisitos, planejamento, implementação, revisão ou documentação
- templates e formatos mínimos de entrada e saída
- validações automatizáveis de completude ou consistência
- integração limitada com tickets, PRs, docs ou pipelines

### Sinais positivos
- redução de variabilidade em artefatos
- melhoria de throughput em etapas delimitadas
- início de uso de critérios de aceite mais explícitos

### Riscos dominantes
- cada fluxo virar uma automação isolada
- falta de identidade comum entre etapas
- ausência de mecanismo claro para exceções e escalonamento

### Critério de passagem
### Inferência
Só vale avançar quando os principais workflows assistidos já produzem artefatos comparáveis, possuem controles mínimos e começam a expor onde os handoffs falham.

## Nível 3. Orquestração parcial
### Descrição
Especialistas atuam em sequência com checkpoints explícitos.

### Capacidades típicas
- especialistas com escopo relativamente delimitado
- contratos básicos de etapa e handoff
- checkpoints humanos em mudanças relevantes
- alguma coordenação entre contexto, execução e validação
- início de observabilidade por fluxo ou etapa

### Sinais positivos
- menos retrabalho na transição entre etapas
- maior clareza sobre ownership e exceções
- possibilidade de comparar resultados entre rotas parecidas

### Riscos dominantes
- o orquestrador absorver responsabilidades de execução demais
- especialistas extrapolarem escopo por falta de contratos melhores
- governança existir de forma desigual entre fluxos

### Critério de passagem
### Inferência
Só vale avançar quando já houver separação nítida entre coordenação e execução, checkpoints orientados a risco e evidência suficiente para explicar por que um fluxo funcionou ou falhou.

## Nível 4. Orquestração ponta a ponta governada
### Descrição
Fluxos SDLC cobertos por contratos, observabilidade, métricas e alçadas.

### Capacidades típicas
- control plane com identidade de fluxo, políticas e trilha de decisão
- handoffs formais entre múltiplas etapas do SDLC
- matriz de autonomia por risco e reversibilidade
- evidência, exceção e aprovação como entidades explícitas
- integração mais ampla com backlog, git, CI/CD, docs e superfícies operacionais

### Sinais positivos
- leitura sistêmica de qualidade, custo, risco e retrabalho
- capacidade de auditar decisões materiais
- uso consistente de checkpoints humanos nos pontos certos, e não só no final

### Riscos dominantes
- elevar autonomia sem calibragem real
- tratar observabilidade técnica como substituto de evidência decisória
- expandir escopo sem consolidar contratos e taxonomia operacional

### Critério de passagem
### Inferência
Só vale avançar quando a plataforma já conseguir operar jornadas ponta a ponta com governança explícita, explicabilidade suficiente e resultados comparáveis entre classes de fluxo.

## Nível 5. Plataforma adaptativa
### Descrição
O sistema aprende com execução, políticas e resultados sem perder governança humana.

### Capacidades típicas
- ajuste progressivo de alçadas com base em risco e evidência
- comparação entre rotas, especialistas, políticas e modelos
- aprendizado institucional a partir de exceções, incidentes e pós-mortem
- benchmarking interno entre times, fluxos e contextos

### Sinais positivos
- autonomia cresce junto com a qualidade do controle
- políticas e rotas são refinadas com base em evidência acumulada
- a plataforma melhora o sistema de entrega, não apenas tarefas individuais

### Riscos dominantes
- feedback loops mal calibrados
- excesso de confiança em métricas incompletas
- degradação gradual da separação entre autonomia operacional e autoridade decisória humana

### Critério de sustentação
### Inferência
Neste nível, o desafio deixa de ser subir de estágio e passa a ser manter adaptação sem corroer governança, segregação de funções e auditabilidade.

## Regras transversais do roadmap
### Proposta conceitual
Independentemente do nível, quatro regras devem permanecer constantes:
1. crescimento de autonomia exige crescimento proporcional de evidência e controle
2. contratos e handoffs devem amadurecer antes da expansão massiva de especialistas
3. checkpoint humano deve migrar para pontos de maior risco, não desaparecer
4. medição deve sair de produtividade local e caminhar para qualidade sistêmica

## Leitura decisória do roadmap
### Inferência
A implicação prática mais importante é que Murilo não deveria perseguir uma plataforma “nível 5” cedo demais. O caminho mais coerente é construir primeiro a capacidade de governar bem fluxos reais, com poucos especialistas, handoffs explícitos, política visível e trilha de evidência suficiente para aprender com execução.

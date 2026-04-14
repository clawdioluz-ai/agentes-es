# Modelo de domínio conceitual

## Objetivo
Explicitar os objetos de domínio que a plataforma precisa tratar como canônicos para coordenar trabalho, governança, evidência e supervisão humana ao longo do ciclo de delivery.

## Resposta curta
O domínio central da plataforma não é “prompt”, “agent run” ou “chat session”. O domínio central é **trabalho governado orientado a missão**. Por isso, os objetos mais importantes são os que tornam intenção, decomposição, transição, decisão e evidência legíveis.

## Tese de modelagem
### Proposta conceitual
O modelo conceitual deve ser centrado em três eixos conectados:
1. **trabalho**: mission, workflow, task
2. **governança**: review, approval, policy, exception
3. **evidência operacional**: artifact, evidence, handoff, execution record

### Inferência
Essa modelagem reforça a principal tese do repositório: o valor da plataforma não está no especialista isolado, mas no sistema que organiza e governa trabalho entre especialistas, humanos e ferramentas.

## Objetos canônicos

## 1. Mission
### Definição
A unidade superior de trabalho orientada a resultado.

### Papel
Conectar intenção, contexto, owner, criticidade, critérios de sucesso e resultado final.

### Campos conceituais mínimos
- identidade
- objetivo
- solicitante e owner
- criticidade, risco e reversibilidade
- estado agregado
- políticas aplicáveis
- outcomes esperados
- evidências finais

## 2. Workflow
### Definição
A malha governada que descreve como uma mission se decompõe e progride.

### Papel
Representar ordem, dependência, branching, joins, waits, retries, checkpoints e caminhos alternativos.

## 3. Task
### Definição
A menor unidade de trabalho que ainda faz sentido para contrato, ownership e avaliação.

### Papel
Delimitar objetivo local, entradas, saídas, autonomia permitida e critérios de aceite.

## 4. Handoff
### Definição
A transferência formal de responsabilidade, contexto e expectativa entre etapas, especialistas ou humanos.

### Papel
Fazer a transição ser explícita e auditável, e não apenas implícita dentro de uma cadeia de mensagens.

## 5. Review
### Definição
Momento formal de avaliação de saída ou decisão.

### Papel
Comparar resultado produzido com contrato, critérios de aceite, qualidade e política.

## 6. Approval
### Definição
Autorização explícita para avançar, executar ação crítica ou encerrar trabalho.

### Papel
Separar avaliação de autorização, evitando confusão entre revisar e aprovar.

## 7. Artifact
### Definição
Objeto de trabalho produzido, transformado, referenciado ou validado na missão.

### Papel
Dar materialidade ao trabalho. Exemplos: brief, requisito, ADR, diff, teste, plano, relatório, changelog.

## 8. Evidence
### Definição
Base verificável que sustenta decisão, transição de estado, review, approval ou conclusão.

### Papel
Permitir explicação posterior e reduzir arbitrariedade nas promoções de estado.

## 9. Policy
### Definição
Conjunto de regras e limites que modulam autonomia, acesso, approvals e exceções.

### Papel
Traduzir governança organizacional em restrições operacionais aplicáveis ao fluxo.

## 10. Exception
### Definição
Situação em que o fluxo sai do caminho normal previsto por falha, conflito, bloqueio, baixa confiança ou violação de política.

### Papel
Tratar exceção como objeto governável, e não mero log técnico.

## 11. Agent
### Definição
Entidade executora, revisora ou aprovadora, humana ou automatizada, que atua sob um papel delimitado.

### Papel
Representar capacidade e responsabilidade, não necessariamente implementação específica.

## 12. Integration capability
### Definição
Capacidade mediada pela plataforma para agir sobre sistemas externos do SDLC.

### Papel
Separar o que é domínio interno da plataforma do que é ação realizada sobre ferramentas externas.

## Relações centrais
### Proposta conceitual
- uma **mission** contém um ou mais **workflows**
- um **workflow** coordena várias **tasks**
- uma **task** pode produzir ou consumir **artifacts**
- transições relevantes acontecem por **handoffs**
- **reviews** avaliam saídas ou decisões
- **approvals** autorizam transições críticas
- **policies** modulam autonomia, acesso e checkpoints
- **evidence** sustenta review, approval e conclusão
- **exceptions** interrompem ou redirecionam o fluxo normal
- **agents** executam papéis sobre tasks, reviews e approvals
- **integration capabilities** conectam artifacts e ações a sistemas externos

## Distinções importantes

## 1. Artifact não é evidence
### Inferência
Nem todo artefato é evidência suficiente. Um diff existe como artifact; ele só vira evidence de qualidade quando associado, por exemplo, a testes, revisão ou política satisfeita.

## 2. Review não é approval
### Inferência
A plataforma precisa manter esses conceitos separados para preservar governança e segregação de funções.

## 3. Task não é step microscópico de runtime
### Inferência
Task deve permanecer legível e governável por humanos. Passos internos do especialista podem existir, mas não devem contaminar o modelo canônico.

## 4. Agent não é o centro do domínio
### Inferência
Agent é relevante, mas subordinado ao trabalho. O modelo da plataforma deve ser work-centric, não agent-centric.

## Limites do modelo
### Alerta de desenho
O modelo deve evitar dois extremos:
- ser genérico demais, virando glossário abstrato
- ser detalhado demais, congelando cedo escolhas de implementação

## Conclusão
### Recomendação
A próxima fase deve consolidar esse domínio como o núcleo semântico do control plane. É ele que permite coerência entre arquitetura, UX operacional, governança e integração com o SDLC.

## Referências
- `docs/30-framework/03-work-management-model.md`
- `docs/40-orchestration/04-target-architecture-proposal.md`
- `docs/40-orchestration/06-platform-blueprint.md`
- `docs/90-adrs/ADR-002-mission-workflow-task-object-model.md`
- `docs/90-adrs/ADR-003-human-in-the-loop-governance.md`
- `docs/90-adrs/ADR-006-evidence-and-auditability-first-class.md`

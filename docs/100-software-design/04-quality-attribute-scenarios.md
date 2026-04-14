# Cenários de atributos de qualidade

## Objetivo
Traduzir princípios centrais do repositório em cenários de qualidade que orientem decisões arquiteturais futuras e permitam revisar a plataforma por algo mais concreto do que preferências de desenho.

## Resposta curta
Para esta plataforma, os atributos mais críticos não são apenas desempenho e escalabilidade. Os atributos que mais distinguem o sistema são:
- governabilidade
- auditabilidade
- confiabilidade operacional
- segurança e isolamento
- extensibilidade
- observabilidade
- eficiência de custo

## Estrutura de cenário adotada
Cada cenário abaixo usa a forma:
- fonte do estímulo
- estímulo
- contexto
- artefato afetado
- resposta esperada
- medida de resposta

## 1. Governabilidade por risco
### Cenário
- **fonte do estímulo**: control plane ou política corporativa
- **estímulo**: uma task tenta executar ação classificada como crítica ou pouco reversível
- **contexto**: missão em andamento, com especialista apto tecnicamente, mas sem alçada plena
- **artefato afetado**: transição de estado da task ou workflow
- **resposta esperada**: a plataforma bloqueia a execução autônoma, exige review ou approval apropriado e registra justificativa
- **medida de resposta**: nenhuma ação crítica avança sem checkpoint exigido; toda exceção gera trilha auditável e identidade do aprovador

### Implicação arquitetural
Policy e approval não podem estar escondidos em prompts ou regras locais de especialistas.

## 2. Auditabilidade de decisão material
### Cenário
- **fonte do estímulo**: auditor, revisor ou owner da mission
- **estímulo**: solicitação para explicar por que uma decisão ou transição crítica ocorreu
- **contexto**: fluxo já concluído ou em revisão posterior
- **artefato afetado**: evidence log e decision trail
- **resposta esperada**: a plataforma reconstrói decisão, contexto relevante, evidências consideradas, responsáveis e políticas aplicadas
- **medida de resposta**: decisões críticas podem ser explicadas sem depender de memória informal de indivíduos

### Implicação arquitetural
Evidência, estado e justificativa precisam ser objetos de primeira classe.

## 3. Confiabilidade operacional em fluxos longos
### Cenário
- **fonte do estímulo**: falha de infraestrutura, timeout externo ou indisponibilidade temporária
- **estímulo**: interrupção durante workflow com waits, handoffs e dependências externas
- **contexto**: missão de longa duração, parcialmente executada
- **artefato afetado**: estado do workflow e tasks correlatas
- **resposta esperada**: a plataforma retoma a execução a partir do estado persistido, sem duplicar transições críticas nem perder checkpoints já realizados
- **medida de resposta**: retomada controlada após falha, com consistência de estado e sem promoção indevida de etapas

### Implicação arquitetural
Durabilidade precisa residir em backbone apropriado, não na memória efêmera do runtime cognitivo.

## 4. Segurança e isolamento contextual
### Cenário
- **fonte do estímulo**: especialista, operador ou integração externa
- **estímulo**: tentativa de acesso a dados, ferramentas ou memória fora do escopo autorizado
- **contexto**: execução multi-contexto, com diferentes sensibilidades e políticas
- **artefato afetado**: memória governada, ferramentas e integrações
- **resposta esperada**: a plataforma restringe acesso segundo mínimo privilégio, redige quando necessário e registra tentativa ou exceção
- **medida de resposta**: especialistas só acessam contexto e ferramentas autorizados por etapa, missão e política

### Implicação arquitetural
Memória precisa ser separada por tipo, sensibilidade e proveniência.

## 5. Extensibilidade sem reescrever o núcleo
### Cenário
- **fonte do estímulo**: equipe de plataforma
- **estímulo**: inclusão de novo especialista, novo conector ou novo provedor de modelo
- **contexto**: plataforma já operando com contratos canônicos estáveis
- **artefato afetado**: runtime de especialistas ou integration gateway
- **resposta esperada**: a nova capacidade é adicionada por interfaces existentes, sem refatorar o modelo canônico de missão, workflow, evidência e policy
- **medida de resposta**: expansão ocorre por composição, com impacto localizado e sem alterar o centro semântico da plataforma

### Implicação arquitetural
Contratos do control plane precisam ser mais estáveis do que os adaptadores das bordas.

## 6. Observabilidade de trajetória, não só de resultado
### Cenário
- **fonte do estímulo**: operador humano ou time de melhoria contínua
- **estímulo**: necessidade de entender gargalos, custo, latência, falhas e baixa confiança em fluxos reais
- **contexto**: múltiplas missões em andamento ou concluídas
- **artefato afetado**: traces, métricas, avaliações e filas operacionais
- **resposta esperada**: a plataforma mostra percurso da missão, tempos por etapa, handoffs, checkpoints, custos e pontos de exceção
- **medida de resposta**: fluxos podem ser comparados e inspecionados sem leitura artesanal de logs dispersos

### Implicação arquitetural
Observabilidade deve tratar missão, task, handoff, review e approval como objetos observáveis.

## 7. Eficiência de custo em uso de modelos e ferramentas
### Cenário
- **fonte do estímulo**: operação da plataforma
- **estímulo**: crescimento de volume ou aumento de custo por execução
- **contexto**: múltiplos especialistas, retries, chamadas a modelos e integrações
- **artefato afetado**: política de despacho e seleção de execução
- **resposta esperada**: a plataforma aplica rotas mais econômicas quando risco e criticidade permitem, preservando qualidade mínima exigida
- **medida de resposta**: custo por missão e por classe de fluxo torna-se monitorável e passível de otimização governada

### Implicação arquitetural
Custo precisa aparecer como métrica de plataforma, não como externalidade invisível.

## Tensões entre atributos
### Inferência
Os atributos mais importantes aqui não são independentes:
- mais autonomia pode reduzir custo e tempo, mas aumentar risco governamental
- mais checkpoints pode melhorar controle, mas degradar tempo de ciclo
- mais memória pode aumentar qualidade local, mas elevar exposição e opacidade
- mais modularidade pode facilitar extensão, mas aumentar complexidade operacional

## Conclusão
### Recomendação
A próxima fase deve tratar esses cenários como critérios de revisão de arquitetura. Eles são a ponte entre a tese do repositório e futuras decisões de stack, contracts e operação.

## Referências
- SEI background sobre quality attribute scenarios e documentation: https://www.sei.cmu.edu/library/documenting-software-architectures-views-and-beyond-second-edition/
- Thoughtworks, architectural fitness function: https://www.thoughtworks.com/en-us/radar/techniques/architectural-fitness-function
- `docs/50-governance/01-governance-security-quality-metrics.md`
- `docs/50-governance/02-measurement-benchmarking-and-evidence.md`
- `docs/90-adrs/ADR-003-human-in-the-loop-governance.md`
- `docs/90-adrs/ADR-006-evidence-and-auditability-first-class.md`

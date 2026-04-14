# Proposta consolidada de framework

## Objetivo
Definir um framework conceitual consolidado para futura criação de agentes, skills e fluxos capazes de cobrir o SDLC ponta a ponta com governança, observabilidade e orquestração robusta.

## Como ler este documento
- **Fato observado**: sustentado por benchmark e fontes citadas em outros capítulos.
- **Inferência**: síntese derivada do benchmark comparativo.
- **Proposta conceitual**: desenho deste repositório para organizar o espaço de solução.
- **Recomendação de desenho futuro**: direção sugerida para a próxima fase arquitetural, sem implementação nesta etapa.

## Síntese de partida

### Fatos observados
- Plataformas mais maduras publicamente conectam IA a artefatos nativos do trabalho, como issue, PR, MR, documentação, pipeline, approvals, logs e telemetry.
- O controle humano continua embutido em pontos críticos de revisão, aprovação, política, segurança e release.
- Contexto compartilhado e governado aparece como ativo central para aumentar qualidade e reduzir erros de coordenação.

### Inferência
O framework reutilizável mais promissor não é um catálogo de agentes isolados. É um sistema de coordenação que separa claramente plano de controle, especialistas executores, artefatos de handoff, políticas, checkpoints humanos e evidência auditável.

## Problema que o framework precisa resolver

### Inferência
Sem um framework explícito, programas de agentic software engineering tendem a cair em pelo menos um destes anti-padrões:
- automação local forte com perda de governança sistêmica
- especialistas com fronteiras borradas e responsabilidades duplicadas
- handoffs implícitos baseados em contexto conversacional frágil
- ausência de critérios formais para escalonamento humano
- medição restrita a velocidade de geração ou volume de tickets

## Proposta consolidada

### Proposta conceitual
O framework é organizado em **oito camadas integradas**.

### 1. Camada de intenção e escopo
Define o objetivo do fluxo, restrições, políticas iniciais, risco, stakeholders, critérios de sucesso e fronteiras da autonomia.

**Funções centrais**
- estruturar a demanda original
- identificar ambiguidades materiais
- converter pedidos soltos em brief operacional
- classificar criticidade, sensibilidade e reversibilidade

### 2. Camada de contexto e memória operacional
Consolida o contexto necessário ao fluxo, com proveniência e escopo de acesso controlado.

**Objetos típicos**
- backlog, issue, epic, ticket
- código e histórico
- ADRs e documentação
- políticas, checklists e exceções
- telemetry, incidentes e feedback operacional

### 3. Camada de planejamento do fluxo
Transforma intenção em plano executável por especialistas.

**Funções centrais**
- decompor objetivo em etapas
- declarar dependências
- decidir serialização ou paralelismo
- fixar pré-condições e pós-condições
- anexar checkpoints previstos

### 4. Camada de orquestração
Coordena execução, estado, conflitos, exceções e rastreabilidade.

**Funções centrais**
- selecionar especialistas por capacidade e risco
- distribuir contratos de etapa
- consolidar outputs e evidências
- controlar estados do fluxo
- abrir escalonamento humano quando necessário

### 5. Camada de especialistas
Reúne agentes ou skills com escopo delimitado e contrato explícito.

**Exemplos de especialistas**
- analista de requisitos
- arquiteto
- implementador
- verificador de testes
- verificador de segurança
- avaliador de risco
- sintetizador de evidência

### 6. Camada de artefatos e contratos
Padroniza a circulação do trabalho entre etapas.

**Objetos de primeira classe**
- brief
- plano
- contrato de etapa
- artefato de saída
- evidência de validação
- decisão
- exceção
- aprovação

### 7. Camada de governança e policy
Impõe limites operacionais e obrigações de controle.

**Componentes típicos**
- políticas por classe de ação
- controles de acesso e redaction
- alçadas de autonomia
- checkpoints humanos obrigatórios
- retenção e auditoria

### 8. Camada de observabilidade e avaliação
Mede resultado sistêmico, não apenas produtividade local.

**Dimensões centrais**
- fluxo
- qualidade
- risco
- retrabalho
- custo
- supervisão humana
- aderência a contrato
- confiança declarada versus resultado observado

## Entidades conceituais mínimas

### Proposta conceitual
O framework deve tratar as seguintes entidades como nativas:
- solicitante
- patrocinador ou dono do problema
- orquestrador
- especialista
- avaliador
- aprovador humano
- artefato
- contrato
- checkpoint
- política
- evidência
- exceção
- decisão
- estado do fluxo

## Relações entre entidades

### Proposta conceitual
1. O **solicitante** inicia uma intenção.
2. O **orquestrador** a converte em fluxo governado.
3. Cada **especialista** recebe contrato explícito.
4. Cada transição produz ou consome **artefatos**.
5. Toda validação material gera **evidência**.
6. Toda divergência relevante produz **exceção** ou **escalonamento**.
7. Toda etapa crítica pode exigir **checkpoint humano**.
8. Toda decisão material deve ser vinculada a política, evidência e confiança.

## Princípios operacionais consolidados

### Inferência
A síntese do benchmark sugere oito princípios de desenho duráveis.

1. **Orquestração antes de automação indiscriminada**  
   A pergunta principal é como coordenar bem, não apenas como gerar mais rápido.

2. **Especialistas desacoplados**  
   O sistema deve preferir especialistas substituíveis a um superagente opaco.

3. **Contratos explícitos em cada handoff**  
   Entrada, saída, critérios de aceite e condições de escalonamento precisam ser declarados.

4. **Contexto com proveniência e escopo**  
   Nem todo especialista deve ver tudo, e toda memória relevante deve ser verificável.

5. **Supervisão humana orientada a risco**  
   Aprovação não é ruído; é parte da arquitetura de controle.

6. **Observabilidade nativa**  
   O fluxo deve ser visível por etapa, decisão, artefato, custo, risco e retrabalho.

7. **Governança incorporada, não periférica**  
   Policies, logs, approvals e evidência precisam existir dentro do fluxo.

8. **Avaliação sistêmica**  
   O framework deve otimizar qualidade, segurança e coordenação, não apenas throughput local.

## Modelo de fluxo do framework

### Proposta conceitual
Cada fluxo ponta a ponta deve percorrer, em termos conceituais, as seguintes macrofases:
1. intenção e qualificação
2. estruturação de contexto
3. planejamento do fluxo
4. execução por especialistas
5. validação e consolidação
6. checkpoint e decisão
7. integração com superfícies nativas do SDLC
8. observação de resultado e aprendizado

## Regras de separação entre orquestrador e especialistas

### Proposta conceitual
O orquestrador **não deve**:
- acumular aprovação final e execução sem contrapeso
- reescrever continuamente contratos já emitidos sem registrar revisão
- esconder incerteza ou conflito entre resultados

O especialista **não deve**:
- extrapolar escopo sem solicitar novo contrato
- autoaprovar sua própria saída em etapas críticas
- tratar contexto inferido como autorização implícita

## Tensões estruturais que o framework precisa administrar

### Inferência
Há cinco tensões permanentes:
- velocidade local versus governança sistêmica
- autonomia versus reversibilidade
- contexto amplo versus mínimo privilégio
- flexibilidade do fluxo versus padronização auditável
- produtividade percebida versus qualidade operacional real

## O que este framework deliberadamente não faz nesta fase

### Proposta conceitual
Este documento não define:
- runtime específico
- protocolo técnico final
- estrutura de classes ou serviços
- schemas executáveis
- automações funcionais
- implementação de agentes ou integrações

## Recomendações de desenho futuro

### Recomendação de desenho futuro
Na próxima fase, o framework deveria ser refinado em quatro artefatos arquiteturais:
1. **modelo formal de contrato de etapa**
2. **modelo formal de artefato e evidência**
3. **matriz de alçadas de autonomia por risco**
4. **modelo de estado do fluxo e de exceções**

### Recomendação de desenho futuro
A futura arquitetura deve ser validada contra cenários de ponta a ponta, por exemplo:
- nova feature com impacto moderado
- correção crítica de segurança
- refatoração com múltiplos times
- incidente em produção com rollback e aprendizado

## Conclusão

### Inferência
A contribuição mais útil deste repositório não é prever qual fornecedor vencerá, mas consolidar um framework neutro que preserve o que há de mais sólido nas evidências públicas: contexto forte, especialistas delimitados, handoffs explícitos, governança embutida e checkpoints humanos orientados a risco.

### Proposta conceitual
O framework consolidado deve funcionar como base para futura arquitetura de agentes/skills ponta a ponta sem depender de um único modelo, produto ou plataforma.
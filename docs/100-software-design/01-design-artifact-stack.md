# Pilha de artefatos de design

## Objetivo
Definir quais artefatos de design a próxima fase deve produzir para reduzir ambiguidade arquitetural sem cair cedo demais em implementação.

## Resposta curta
A próxima fase deve trabalhar com uma pilha pequena, cumulativa e conectada de artefatos.

## Artefatos candidatos
### 1. Documento de contexto e fronteiras
- objetivo do sistema
- usuários e sistemas externos
- limites explícitos do produto
- integrações e dependências críticas

### 2. Conjunto de visões arquiteturais
- contexto
- contêineres conceituais
- dinâmica principal
- implantação conceitual quando necessário

### 3. Cenários de atributos de qualidade
- segurança
- auditabilidade
- confiabilidade
- extensibilidade
- custo e eficiência operacional

### 4. Modelo de domínio conceitual
- missão
- workflow
- task
- handoff
- approval
- evidence
- artifact
- policy

### 5. Registro de decisões
- decisões estruturantes já tomadas
- decisões em aberto
- tradeoffs e critérios

## Questões a aprofundar
- qual pacote mínimo gera clareza sem excesso documental?
- como ligar views, quality attributes e ADRs?
- quais artefatos servem melhor uma plataforma control-plane-first?

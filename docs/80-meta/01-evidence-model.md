# Modelo de evidência

## Objetivo
Estabelecer uma disciplina explícita para separar, em todo o repositório, o que é evidência observada, o que é inferência analítica, o que é proposta conceitual e o que já é recomendação para uma fase futura de desenho.

## Problema que este modelo resolve

### Inferência
Pesquisas estratégicas sobre IA aplicada ao SDLC costumam misturar quatro coisas diferentes:
- afirmações literalmente sustentadas por fonte
- sínteses derivadas de múltiplas fontes
- invenções organizacionais úteis para estruturar o problema
- recomendações para o que ainda deveria ser desenhado ou implementado

Quando essas camadas são confundidas, o leitor pode interpretar marketing como fato, hipótese como benchmark, ou proposta local como consenso de mercado.

## Quatro categorias obrigatórias

### 1. Fato observado em fonte
#### Definição
Afirmação sustentada diretamente por fonte identificável.

#### Critério de uso
Use esta categoria quando a fonte realmente disser ou demonstrar aquilo, com especificidade suficiente.

#### Exemplos válidos
- “O GitHub afirma que Copilot code review deixa comentários, mas não aprova pull requests.”
- “O GitLab documenta audit event por requisição de API no Software Development Flow.”
- “O Google afirma que prompts e respostas do Gemini Code Assist Enterprise não são usados para treino do modelo.”

#### Erros comuns
- extrapolar além do que a fonte realmente cobre
- converter promessa comercial em comprovação de resultado
- tratar roadmap ou visão como fato operacional consolidado

### 2. Inferência
#### Definição
Conclusão derivada de múltiplos fatos observados, sem declaração literal equivalente nas fontes.

#### Critério de uso
Use esta categoria quando a conclusão fizer sentido analítico, mas for uma síntese do pesquisador e não uma citação direta.

#### Exemplos válidos
- “A maturidade pública está mais forte em copilots e fluxos delimitados do que em autonomia integral do SDLC.”
- “Contexto compartilhado aparece como ativo competitivo central nas plataformas analisadas.”
- “Governança embutida tende a separar melhor orquestrador e especialista.”

#### Erros comuns
- apresentar inferência como se fosse consenso explícito do mercado
- omitir tensões, lacunas ou contradições entre fontes
- apoiar inferência importante em apenas uma fonte fraca

### 3. Proposta conceitual
#### Definição
Elemento do framework proposto neste repositório para organizar o espaço de solução.

#### Critério de uso
Use esta categoria quando o conteúdo for criação analítica local, mesmo que inspirado pelas evidências.

#### Exemplos válidos
- “Camada de contratos e handoffs como entidade de primeira classe.”
- “Modelo de oito camadas do framework.”
- “Estados conceituais do fluxo ponta a ponta.”

#### Erros comuns
- sugerir que a proposta já é prática dominante no mercado
- esconder que a taxonomia foi criada neste trabalho
- tratar proposta conceitual como requisito técnico já validado empiricamente

### 4. Recomendação de desenho futuro
#### Definição
Sugestão orientada à próxima fase de arquitetura, especificação ou implementação.

#### Critério de uso
Use esta categoria quando o texto estiver dizendo o que deveria ser feito depois, e não descrevendo estado atual.

#### Exemplos válidos
- “Formalizar schema de contrato de etapa na próxima fase.”
- “Validar a arquitetura contra cenários de incidentes e rollback.”
- “Definir matriz de autonomia por risco.”

#### Erros comuns
- escrever recomendações em tom de fato já estabelecido
- antecipar implementação sem base suficiente
- misturar recomendação com benchmark de fornecedor

## Regra operacional para todos os documentos

### Proposta conceitual
Todo documento analítico deste repositório deve, sempre que relevante:
1. marcar explicitamente a categoria predominante de cada seção
2. evitar parágrafos híbridos em que fato, inferência e proposta apareçam sem distinção
3. usar citação clara quando fizer afirmação factual material
4. nomear como recomendação apenas o que pertence à fase seguinte

## Hierarquia de confiança

### Proposta conceitual
Quando houver dúvida sobre qual rótulo usar, adotar a hierarquia mais conservadora:
- se a fonte sustenta diretamente, usar **fato observado**
- se depende de síntese, usar **inferência**
- se é desenho do repositório, usar **proposta conceitual**
- se aponta para o próximo passo, usar **recomendação de desenho futuro**

## Testes práticos de classificação

### Proposta conceitual
Antes de rotular um trecho, aplicar estas perguntas:

### Teste 1, “a fonte realmente diz isso?”
Se sim, tende a ser **fato observado**.

### Teste 2, “precisei combinar várias fontes para chegar aqui?”
Se sim, tende a ser **inferência**.

### Teste 3, “isso é uma estrutura inventada neste repositório para organizar a solução?”
Se sim, tende a ser **proposta conceitual**.

### Teste 4, “isso ainda pertence à próxima fase de desenho ou implementação?”
Se sim, tende a ser **recomendação de desenho futuro**.

## Regras de redação

### Proposta conceitual
- Fatos devem vir acompanhados de fonte identificável.
- Inferências devem indicar base comparativa suficiente.
- Propostas conceituais devem assumir sua autoria local de forma transparente.
- Recomendações futuras devem evitar linguagem que simule decisão já tomada.

## Casos limítrofes

### Inferência
Alguns trechos podem nascer como fato local e virar inferência sistêmica. Exemplo: uma plataforma documenta approvals; várias plataformas documentam approvals ou gates humanos; a conclusão de que “controle humano continua embutido no fluxo oficial” já é inferência.

### Proposta conceitual
Também é possível que uma proposta conceitual seja fortemente inspirada por fatos observados, mas isso não a transforma em fato. Inspiração não equivale a validação empírica.

## Aplicação a este repositório

### Fato observado
Os capítulos de benchmarking e bibliografia concentram mais conteúdo factual.

### Inferência
Os capítulos de síntese, padrões e comparação concentram mais inferências.

### Proposta conceitual
Os capítulos de framework, handoffs e orquestração concentram mais proposta conceitual.

### Recomendação de desenho futuro
Os capítulos de roadmap e próximos passos concentram mais recomendações para a fase seguinte.

## Benefícios do modelo

### Inferência
Essa separação reduz quatro riscos recorrentes:
- confundir benchmark com blueprint
- confundir marketing com evidência consolidada
- confundir taxonomia local com padrão de mercado
- confundir sugestão futura com decisão arquitetural já validada

## Conclusão

### Proposta conceitual
Este modelo de evidência é parte da governança intelectual do repositório. Ele existe para manter a pesquisa honesta, auditável e útil como base para uma fase futura de desenho, sem antecipar implementação nem inflar o que as fontes realmente provam.
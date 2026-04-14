# Padrões benchmarked com fontes

## Objetivo
Consolidar padrões recorrentes observados em fontes primárias e quase primárias sobre IA generativa e fluxos agentic no SDLC.

## Leitura do documento
- **Fato observado**: sustentado diretamente por fonte listada.
- **Inferência**: síntese derivada de múltiplas fontes.
- **Implicação para o framework**: proposta conceitual deste repositório.

## Padrão 1, adoção mais madura perto do código do que da orquestração ponta a ponta

### Fatos observados
- O GitHub documenta Copilot Code Review como revisão de pull request com comentários e sugestões aplicáveis, mantendo a aprovação final fora do agente. Fonte: GitHub Docs, "Using GitHub Copilot code review", 2026, https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review
- O GitHub reporta que o recurso já responde por mais de um em cada cinco code reviews na plataforma e descreve uma arquitetura agentic focada em contexto de repositório, memória e feedback loop contínuo. Fonte: GitHub Blog, "60 million Copilot code reviews and counting", 2026, https://github.blog/ai-and-ml/github-copilot/60-million-copilot-code-reviews-and-counting/
- O GitLab descreve seu Software Development Flow como um fluxo no IDE que cria plano, propõe mudanças e usa contexto do projeto, mas dentro de um escopo de tarefa delimitado. Fonte: GitLab Docs, "Software Development Flow", 2026, https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/
- A Atlassian posiciona Rovo Dev CLI como assistente contextual para entender código, implementar features, gerar documentação e apoiar migrações, integrado ao terminal e ao ecossistema Atlassian. Fonte: Atlassian Blog, "Rovo Dev agent, now available in the CLI", 2026, https://www.atlassian.com/blog/announcements/rovo-dev-command-line-interface

### Inferência
A maturidade pública mais tangível está em tarefas de desenvolvimento, revisão, testes, documentação e reparo de pipeline. Há menos evidência pública detalhada de automação totalmente fechada e confiável do SDLC inteiro.

### Implicação para o framework
O framework deve assumir que a progressão realista começa por fluxos compostos de alta supervisão e não por autonomia integral fim a fim.

## Padrão 2, o contexto unificado é tratado como ativo central

### Fatos observados
- O GitHub atribui ganho de qualidade da revisão ao uso de contexto de repositório, linked issues, histórico e memória entre revisões. Fonte: GitHub Blog, 2026, https://github.blog/ai-and-ml/github-copilot/60-million-copilot-code-reviews-and-counting/
- O GitLab afirma que o Software Development Flow entende estrutura do projeto, código e histórico, além de aceitar contexto adicional como issues e merge requests. Fonte: GitLab Docs, 2026, https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/
- A Atlassian afirma que Teamwork Graph funciona como camada de inteligência de dados, unificando dados de Atlassian e de mais de 100 apps, aprendendo contexto e aplicando checagens de acesso de última milha. Fonte: Atlassian, "Teamwork Graph", 2026, https://www.atlassian.com/platform/teamwork-graph

### Inferência
Os fornecedores mais avançados tratam contexto compartilhado, não apenas o modelo, como principal insumo de coordenação entre agentes e etapas.

### Implicação para o framework
A arquitetura futura deve prever um plano explícito de contexto com proveniência, escopo de acesso, versionamento e políticas de compartilhamento por etapa.

## Padrão 3, o controle humano continua embutido no fluxo oficial

### Fatos observados
- O GitHub afirma que Copilot deixa apenas comentário, não aprova nem bloqueia merge, e portanto não substitui o revisor humano requerido. Fonte: GitHub Docs, 2026, https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review
- O GitLab documenta que o fluxo gera mudanças propostas e o usuário controla quando aceitá-las, modificá-las ou rejeitá-las. Fonte: GitLab Docs, 2026, https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/
- A Thoughtworks argumenta que AI-first software delivery exige supervisão rigorosa de engenharia para evitar dívida técnica, vulnerabilidades e requisitos alucinados. Fonte: Thoughtworks, "AI and software delivery", 2026, https://www.thoughtworks.com/en-us/insights/looking-glass/looking-glass-2026/AI-and-software-delivery

### Inferência
O padrão recorrente não é remover humanos, mas deslocá-los para funções de revisão, governança, priorização e exceção.

### Implicação para o framework
Checkpoints humanos devem ser modelados como objetos de governança do fluxo, não como exceções improvisadas.

## Padrão 4, a narrativa de plataforma supera a de agente isolado

### Fatos observados
- O GitLab descreve um modelo de plataforma unificada, com data model único, AI agents, merge requests, CI/CD, security, SBOMs, approvals, telemetry e guardrails. Fonte: GitLab Blog, "Agentic SDLC", 2026, https://about.gitlab.com/blog/agentic-sdlc-gitlab-and-tcs-deliver-intelligent-orchestration-across-the-enterprise/
- A Atlassian conecta Rovo Dev ao Teamwork Graph e às superfícies Jira, Confluence, Bitbucket e Compass. Fontes: Atlassian Blog, 2026, https://www.atlassian.com/blog/announcements/rovo-dev-command-line-interface ; Atlassian Teamwork Graph, 2026, https://www.atlassian.com/platform/teamwork-graph
- A DORA descreve um core model de capacidades, métricas e outcomes para melhoria contínua em software delivery, reforçando visão sistêmica e não apenas ferramental. Fonte: DORA Research, 2026, https://dora.dev/research/

### Inferência
A unidade competitiva emergente é o sistema operacional de engenharia com contexto, políticas, métricas e superfícies integradas, não apenas um copiloto individual.

### Implicação para o framework
O framework deve ser concebido como control plane de fluxo e evidência, capaz de plugar especialistas diversos sem depender de um único fornecedor.

## Padrão 5, benchmarking público ainda mistura marketing, telemetria de produto e evidência científica parcial

### Fatos observados
- O GitHub reporta benefícios em satisfação, foco e redução de esforço cognitivo a partir de survey com mais de 2.000 developers e usa o framework SPACE para discutir produtividade. Fonte: GitHub Blog, "Research: quantifying GitHub Copilot’s impact on developer productivity and happiness", 2022, https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/
- A Microsoft Research publica experimento controlado em que participantes com GitHub Copilot completaram uma tarefa 55,8% mais rápido que o grupo de controle. Fonte: Microsoft Research, "The Impact of AI on Developer Productivity: Evidence from GitHub Copilot", 2023, https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/
- A Atlassian usa SWE-bench como evidência comparativa de capacidade do Rovo Dev CLI. Fonte: Atlassian Blog, 2026, https://www.atlassian.com/blog/announcements/rovo-dev-command-line-interface
- O site do SWE-bench mantém leaderboards oficiais e referencia paper e documentação do benchmark. Fonte: SWE-bench, 2026, https://www.swebench.com/

### Inferência
O mercado já usa três famílias de evidência, produtividade percebida, experimento controlado e benchmark de resolução de issues. Nenhuma, isoladamente, captura orquestração ponta a ponta em contexto empresarial.

### Implicação para o framework
A futura camada de avaliação deve combinar métricas de fluxo, qualidade, risco, esforço humano, aderência a contrato e benchmarks externos quando aplicáveis.

## Síntese final
### Fatos observados
O estado da arte publicamente documentado converge para agentes com forte contexto, escopo delimitado, guardrails, auditabilidade e integração com superfícies existentes de engenharia.

### Inferência
A pergunta estratégica deixa de ser "qual agente gera mais código" e passa a ser "qual sistema coordena melhor contexto, handoffs, controles e aprendizado ao longo do SDLC".

### Implicação para o framework
Este repositório deve privilegiar arquitetura de orquestração, contratos e evidência operacional acima de automação maximalista.
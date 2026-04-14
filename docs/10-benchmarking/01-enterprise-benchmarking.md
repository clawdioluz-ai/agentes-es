# Benchmarking aprofundado de empresas e plataformas

## Objetivo
Comparar, empresa por empresa, como os principais atores públicos do mercado estão posicionando IA generativa e fluxos agentic ao longo do SDLC, com ênfase em orquestração, governança e superfícies de controle.

## Como ler este documento
- **Fato observado**: sustentado diretamente por fonte citada.
- **Inferência**: síntese comparativa a partir de múltiplas fontes.
- **Proposta conceitual**: não usada neste documento, reservada aos capítulos de framework.

## Critérios comparativos
1. **Amplitude no SDLC**: em quantas etapas a oferta ou operating model aparece publicamente.
2. **Forma de coordenação**: copiloto local, fluxo estruturado, multiagente ou plataforma.
3. **Superfície de controle**: PR/MR, issue, pipeline, ticket, documentação, runtime, telemetry.
4. **Governança explícita**: approvals, audit log, policy, acesso, data controls, risk controls.
5. **Contexto compartilhado**: repositório, histórico, linked issues, knowledge graph, docs, dados corporativos.
6. **Força da evidência pública**: alta, média ou baixa, conforme especificidade e primariedade das fontes.

## Resumo executivo

### Fatos observados
- GitHub, GitLab e Atlassian já descrevem publicamente fluxos agentic conectados a artefatos nativos do trabalho de engenharia, como pull requests, merge requests, issues, documentação, pipeline e contexto de repositório. Fontes: GitHub Docs e Blog; GitLab Docs e Blog; Atlassian Blog e Teamwork Graph.
- Google, AWS e Microsoft enfatizam apoio mais amplo ao SDLC e controles corporativos de governança, mas com menos transparência pública sobre handoffs detalhados entre especialistas ao longo de um fluxo ponta a ponta. Fontes: Google Developers; AWS DevOps Blog; Microsoft Learn.
- Thoughtworks e Accenture oferecem uma leitura estratégica e operacional do problema, insistindo em oversight de engenharia, platform engineering, change management e governança responsável. Fontes: Thoughtworks; Accenture.

### Inferência
A fronteira pública mais madura não é “autonomia completa do SDLC”, mas um stack composto por: contexto compartilhado, agentes especializados de escopo limitado, superfícies nativas de controle e mecanismos explícitos de governança. A diferença entre empresas está menos na retórica de autonomia e mais em qual plano de controle elas já tornaram observável.

## Benchmark por empresa e plataforma

### GitHub
#### Fatos observados
- Copilot Code Review atua sobre pull requests, comenta, sugere mudanças e não conta como aprovação obrigatória, preservando o gate humano de merge. Fonte: GitHub Docs, “Using GitHub Copilot code review”, 2026, https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review
- O GitHub descreve um sistema de memória agentic com citações em locais específicos de código e verificação just-in-time antes do uso da memória. Fonte: GitHub Blog, “Building an agentic memory system for GitHub Copilot”, 2026, https://github.blog/ai-and-ml/github-copilot/building-an-agentic-memory-system-for-github-copilot/

#### Leitura analítica
- **Amplitude no SDLC**: forte em implementação, revisão, correção e contexto de repositório; cobertura pública crescente para segurança, debugging e manutenção.
- **Forma de coordenação**: ecossistema agentic centrado em repositório e PR.
- **Superfície de controle**: PR, review comments, linked issues, memória de repositório.
- **Governança explícita**: média a alta, pois o humano continua no merge e a memória usa verificação em tempo de leitura.
- **Força da evidência pública**: alta.

#### Inferência
O GitHub é hoje uma referência forte para o padrão “agente profundamente embutido em artefatos de código e revisão”, mas ainda com menos transparência pública sobre um control plane corporativo que atravesse backlog, arquitetura, release e operação de forma única.

### GitLab
#### Fatos observados
- O Software Development Flow cria plano, trabalha em etapas, usa contexto do projeto e do histórico, e mantém o usuário no controle para aceitar, modificar ou rejeitar sugestões. Fonte: GitLab Docs, “Software Development Flow”, 2026, https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/
- O fluxo acessa APIs específicas de projetos, busca, pipelines, jobs, merge requests, epics, issues, notes e usage data, e gera audit event para cada requisição. Fonte: GitLab Docs, mesmo link.
- O GitLab posiciona sua plataforma como control plane com unified data model, merge requests, CI/CD, security, SBOMs, approvals, telemetry e policy-aligned workflows. Fonte: GitLab Blog, “Agentic SDLC: GitLab and TCS deliver Intelligent Orchestration across the enterprise”, 2026, https://about.gitlab.com/blog/agentic-sdlc-gitlab-and-tcs-deliver-intelligent-orchestration-across-the-enterprise/

#### Leitura analítica
- **Amplitude no SDLC**: muito forte do planejamento técnico ao pipeline e compliance.
- **Forma de coordenação**: fluxo estruturado no IDE e narrativa explícita de multi-agent orchestration na plataforma.
- **Superfície de controle**: issue, MR, pipeline, job, audit event, approvals, SBOM, telemetry.
- **Governança explícita**: muito alta na documentação pública.
- **Força da evidência pública**: alta.

#### Inferência
Entre as fontes públicas analisadas, o GitLab é o exemplo mais próximo de um plano de controle ponta a ponta explicitamente articulado, porque conecta agentes, artefatos, telemetria e guardrails numa única narrativa operacional.

### Atlassian
#### Fatos observados
- Rovo Dev CLI é apresentado como agente no terminal que entende código, acelera desenvolvimento, ajuda em testes, debugging, documentação e integra Jira, Confluence e Bitbucket. Fonte: Atlassian Blog, “Rovo Dev agent, now available in the CLI”, 2026, https://www.atlassian.com/blog/announcements/rovo-dev-command-line-interface
- A Atlassian afirma que Teamwork Graph é a camada de inteligência de dados da plataforma, unificando dados de Atlassian e de mais de 100 apps, aprendendo contexto e aplicando checagens finais de acesso. Fonte: Atlassian, “Teamwork Graph”, 2026, https://www.atlassian.com/platform/teamwork-graph

#### Leitura analítica
- **Amplitude no SDLC**: forte em entendimento de trabalho, documentação, tickets e fluxo de desenvolvimento conectado.
- **Forma de coordenação**: agente ligado a um grafo/contexto organizacional.
- **Superfície de controle**: terminal, Jira, Confluence, Bitbucket, conectores.
- **Governança explícita**: média, com sinais importantes de permissões, uso e last-mile access checks.
- **Força da evidência pública**: média a alta.

#### Inferência
A Atlassian se diferencia menos por um fluxo técnico fechado e mais por tratar contexto organizacional compartilhado como infraestrutura para agentes. Isso é especialmente relevante para handoffs entre produto, documentação e engenharia.

### Google
#### Fatos observados
- O Google documenta que prompts e respostas do Gemini Code Assist Standard e Enterprise não são usados para treinar os modelos, que os dados são tratados segundo termos e adendos corporativos e que os prompts são criptografados em trânsito. Fonte: Google Developers, “How Gemini Code Assist Standard and Enterprise use your data”, 2026, https://developers.google.com/gemini-code-assist/docs/data-governance
- O Google também explicita que o cliente segue responsável por segurança, testes e efetividade do código gerado. Fonte: mesmo link.

#### Leitura analítica
- **Amplitude no SDLC**: ampla na narrativa pública, mas com menos detalhe operacional público sobre handoffs multiagente.
- **Forma de coordenação**: assistente corporativo com forte ênfase em governança de dados.
- **Superfície de controle**: IDE e integrações de desenvolvimento.
- **Governança explícita**: alta em dados e responsabilidade de uso; média em coordenação ponta a ponta pública.
- **Força da evidência pública**: média.

#### Inferência
O ponto forte público do Google está menos em descrever uma orquestração completa e mais em tornar claro o envelope de privacidade, responsabilidade e customização corporativa do assistente.

### AWS / Amazon
#### Fatos observados
- A AWS afirma que Amazon Q Developer apoia equipes ao longo do SDLC e apresenta exemplos desde planejamento e pesquisa com Amazon Q Business até design, desenvolvimento, testes e manutenção. Fonte: AWS DevOps Blog, “Accelerate your Software Development Lifecycle with Amazon Q”, 2024, https://aws.amazon.com/blogs/devops/accelerate-your-software-development-lifecycle-with-amazon-q/
- A AWS descreve adoção corporativa como problema de change management, exigindo patrocínio executivo, definição de metas e espaço deliberado para aprendizagem. Fonte: AWS DevOps Blog, “Adopting Amazon Q Developer in Enterprise Environments”, 2025, https://aws.amazon.com/blogs/devops/adopting-amazon-q-developer-in-enterprise-environments/

#### Leitura analítica
- **Amplitude no SDLC**: ampla, inclusive requisitos e operação, especialmente quando combinando Q Business e Q Developer.
- **Forma de coordenação**: combinação de assistentes para contexto empresarial e desenvolvimento.
- **Superfície de controle**: documentos internos, wikis, Jira, IDE, manutenção e operação.
- **Governança explícita**: média, com força maior em adoção organizacional do que em contratos técnicos públicos entre agentes.
- **Força da evidência pública**: média.

#### Inferência
A AWS oferece uma visão forte de SDLC ampliado, mas a contribuição pública mais útil para este repositório está em adoção organizacional, integração com conhecimento interno e necessidade de mudança operacional gradual.

### Microsoft
#### Fatos observados
- O Microsoft Learn documenta controles de Copilot Studio como data policies, audit logs em Purview e Sentinel, uso de credenciais do usuário, controles de knowledge sources, connectors, skills, HTTP requests, publication channels e triggers. Fonte: Microsoft Learn, “Security and governance - Microsoft Copilot Studio”, 2026, https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-and-governance
- A Microsoft Research fornece evidência causal de produtividade para Copilot em tarefa delimitada, mostrando melhora de 55,8% no tempo de conclusão. Fonte: Microsoft Research, “The Impact of AI on Developer Productivity: Evidence from GitHub Copilot”, 2023, https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/

#### Leitura analítica
- **Amplitude no SDLC**: forte na camada de governança e em produtividade em tarefas específicas; menos detalhada publicamente, nas fontes analisadas, como orquestração técnica ponta a ponta.
- **Forma de coordenação**: plataforma com controles administrativos fortes.
- **Superfície de controle**: ambientes, conectores, fontes de conhecimento, auditoria, publicação.
- **Governança explícita**: muito alta.
- **Força da evidência pública**: média a alta, dependendo do subtema.

#### Inferência
A Microsoft aparece como referência forte para governança administrativa e mensuração de produtividade, mas menos transparente, nas fontes aqui curadas, sobre contratos operacionais entre especialistas ao longo do SDLC completo.

### Thoughtworks
#### Fatos observados
- A Thoughtworks define AI-first software delivery como integração ponta a ponta de sistemas generativos e agentic no ciclo de requisitos, design, desenvolvimento, testes, deployment e manutenção.
- A mesma fonte insiste que essas capacidades devem operar sob forte engineering oversight para evitar dívida técnica, vulnerabilidades e arquiteturas frágeis. Fonte: Thoughtworks, “AI and software delivery”, 2026, https://www.thoughtworks.com/en-us/insights/looking-glass/looking-glass-2026/AI-and-software-delivery

#### Leitura analítica
- **Amplitude no SDLC**: muito ampla na formulação estratégica.
- **Forma de coordenação**: operating model e disciplina de engenharia, não produto específico.
- **Superfície de controle**: conceitual.
- **Governança explícita**: alta como princípio; baixa como detalhe operacional público.
- **Força da evidência pública**: média.

#### Inferência
A Thoughtworks é valiosa menos como benchmark de produto e mais como benchmark de operating model: end-to-end sim, autonomia irrestrita não.

### Accenture
#### Fatos observados
- A Accenture posiciona GenWizard como plataforma para escalar IA generativa em software development, modernization, application and infrastructure management. Fonte: Accenture, “GenWizard”, 2026, https://www.accenture.com/us-en/services/cloud/application-transformation/genwizard
- A Accenture também publica material específico sobre Responsible AI e governança como base de adoção empresarial. Fonte: Accenture, “Responsible AI”, 2026, https://www.accenture.com/us-en/services/data-ai/responsible-ai

#### Leitura analítica
- **Amplitude no SDLC**: ampla na narrativa corporativa e transformação de delivery.
- **Forma de coordenação**: plataforma e transformação operacional.
- **Superfície de controle**: menos detalhada publicamente nas fontes disponíveis.
- **Governança explícita**: alta no plano de princípios corporativos.
- **Força da evidência pública**: média a baixa para detalhes operacionais, média para direção estratégica.

#### Inferência
A Accenture ajuda a entender como consultorias enquadram o problema: escala organizacional, industrialização e IA responsável. Como benchmark operacional fino de handoffs e contratos, a evidência pública é mais limitada.

## Matriz comparativa consolidada

| Empresa/plataforma | Força principal observável | Superfície de controle dominante | Governança pública | Evidência pública | Leitura síntese |
|---|---|---|---|---|---|
| GitHub | agente embutido em código, PR e memória | PR, review, linked issues, repo memory | média-alta | alta | melhor visibilidade em revisão e contexto de código |
| GitLab | control plane DevSecOps + agentes | issue, MR, pipeline, approvals, telemetry, audit | alta | alta | caso mais completo de orquestração explícita |
| Atlassian | contexto organizacional e grafo de trabalho | Jira, Confluence, Bitbucket, terminal, graph | média | média-alta | forte ponte entre trabalho, docs e engenharia |
| Google | governança de dados e uso corporativo | IDE, personalização, data governance | alta | média | forte em privacidade e responsabilidade de uso |
| AWS | SDLC ampliado + adoção empresarial | docs internos, Jira, IDE, operação | média | média | forte em integração com conhecimento interno e change management |
| Microsoft | controles administrativos e auditoria | data policies, audit, connectors, environments | alta | média-alta | referência importante em controles de plataforma |
| Thoughtworks | operating model AI-first com oversight | princípios e operating model | alta | média | benchmark conceitual de disciplina end-to-end |
| Accenture | transformação em escala e IA responsável | plataforma e governança corporativa | alta | média | benchmark estratégico de industrialização |

## Padrões comparativos mais fortes

### Inferência 1
Plataformas com melhor narrativa pública não vendem apenas geração de código. Elas vendem contexto, governança, integração e controle.

### Inferência 2
A unidade de coordenação mais visível é o artefato nativo do trabalho, como issue, PR, MR, ticket, documentação, pipeline e log, não uma conversa livre desancorada.

### Inferência 3
Os líderes públicos se dividem em dois grupos complementares:
- **plataformas de execução do SDLC**: GitHub, GitLab, Atlassian
- **plataformas e consultorias de governança/adopção**: Google, AWS, Microsoft, Thoughtworks, Accenture

### Inferência 4
Quanto mais a empresa publica detalhes de auditabilidade, políticas e controle de acesso, mais clara fica a separação entre especialista executor e plano de controle.

## Implicações para este repositório

### Inferência
O framework futuro não deve copiar cegamente um único fornecedor. Ele deve combinar:
- profundidade operacional em artefatos e review, visível no GitHub
- control plane explícito e auditável, visível no GitLab
- camada de contexto organizacional compartilhado, visível na Atlassian
- envelope forte de governança de dados e administração, visível em Google e Microsoft
- atenção a change management e adoção organizacional, visível na AWS e nas consultorias

## Conclusão

### Inferência
O benchmark empresa por empresa aponta para uma tese estável: a maturidade relevante para orquestração ponta a ponta não está em um agente “genial”, mas em um sistema que coordena especialistas, contexto, artefatos, políticas, checkpoints humanos e evidência auditável ao longo do fluxo inteiro.
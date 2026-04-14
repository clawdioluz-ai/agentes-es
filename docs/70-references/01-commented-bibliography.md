# Bibliografia e referências comentadas

## Estratégia de curadoria
Priorizar fontes primárias e materiais corporativos ou técnicos de alta credibilidade. Quando a evidência é promocional ou parcialmente comercial, isso é indicado explicitamente.

## Como ler esta bibliografia
- **Tipo**: primária, quase primária, pesquisa aplicada, benchmark, síntese estratégica.
- **Uso preferencial**: para que a fonte é mais confiável neste repositório.
- **Limitação**: onde ela não deve ser superinterpretada.

## A. Plataformas de engenharia, agentes e superfícies de controle

1. **GitHub Docs, Using GitHub Copilot code review**  
   Tipo: primária.  
   URL: https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review  
   Uso preferencial: delimitar o papel do agente no PR, inclusive o fato de que Copilot comenta, mas não aprova nem bloqueia merge.  
   Limitação: documentação de produto, não avaliação independente.

2. **GitHub Blog, Building an agentic memory system for GitHub Copilot**  
   Tipo: quase primária.  
   URL: https://github.blog/ai-and-ml/github-copilot/building-an-agentic-memory-system-for-github-copilot/  
   Uso preferencial: entender memória com citações, verificação just-in-time e compartilhamento de aprendizados entre coding agent, CLI e code review.  
   Limitação: material first-party e recente, sujeito a framing favorável.

3. **GitHub Blog, 60 million Copilot code reviews and counting**  
   Tipo: quase primária.  
   URL: https://github.blog/ai-and-ml/github-copilot/60-million-copilot-code-reviews-and-counting/  
   Uso preferencial: sinais de escala, linked issues, loops de feedback e arquitetura agentic em produção.  
   Limitação: telemetria proprietária e seleção de métricas feita pela própria plataforma.

4. **GitLab Docs, Software Development Flow**  
   Tipo: primária.  
   URL: https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/  
   Uso preferencial: detalhar fluxo estruturado, APIs acessadas, audit log, riscos, escopo de autonomia e artefatos tratados pela plataforma.  
   Limitação: cobre um fluxo fundacional, não a totalidade de todos os operating models possíveis.

5. **GitLab Blog, Agentic SDLC: GitLab and TCS deliver Intelligent Orchestration across the enterprise**  
   Tipo: quase primária.  
   URL: https://about.gitlab.com/blog/agentic-sdlc-gitlab-and-tcs-deliver-intelligent-orchestration-across-the-enterprise/  
   Uso preferencial: control plane, approvals, telemetry, SBOMs, guardrails, unified data model e platform engineering.  
   Limitação: mistura arquitetura conceitual com mensagem comercial.

6. **Atlassian Blog, Rovo Dev agent, now available in the CLI**  
   Tipo: quase primária.  
   URL: https://www.atlassian.com/blog/announcements/rovo-dev-command-line-interface  
   Uso preferencial: integração terminal, Jira, Confluence, Bitbucket, permissões, extensibilidade via MCP e benchmark externo via SWE-bench.  
   Limitação: anúncio de produto, com viés promocional.

7. **Atlassian, Teamwork Graph**  
   Tipo: primária.  
   URL: https://www.atlassian.com/platform/teamwork-graph  
   Uso preferencial: camada de contexto compartilhado, unificação de dados, enriching experiences e last-mile access checks.  
   Limitação: descreve princípios de plataforma e benefícios, mas com pouca telemetria pública detalhada.

## B. Governança, privacidade e controles corporativos

8. **Google Developers, How Gemini Code Assist Standard and Enterprise use your data**  
   Tipo: primária.  
   URL: https://developers.google.com/gemini-code-assist/docs/data-governance  
   Uso preferencial: governança de dados, não uso de prompts/respostas para treino, criptografia em trânsito, responsabilidade do cliente por teste e segurança.  
   Limitação: forte em data governance, menos detalhada em orquestração multiagente ponta a ponta.

9. **Microsoft Learn, Security and governance - Microsoft Copilot Studio**  
   Tipo: primária.  
   URL: https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-and-governance  
   Uso preferencial: data policies, audit logs, conectores, skills, knowledge sources, publication channels e controles administrativos.  
   Limitação: foca governança da plataforma, não um fluxo técnico específico de software engineering ponta a ponta.

10. **Accenture, Responsible AI**  
    Tipo: primária.  
    URL: https://www.accenture.com/us-en/services/data-ai/responsible-ai  
    Uso preferencial: princípios corporativos para IA responsável, governança e confiança organizacional.  
    Limitação: alto nível, com pouco detalhe operacional sobre handoffs do SDLC.

11. **Accenture, GenWizard**  
    Tipo: primária.  
    URL: https://www.accenture.com/us-en/services/cloud/application-transformation/genwizard  
    Uso preferencial: narrativa de escala, industrialização e transformação de software delivery com IA generativa.  
    Limitação: material de oferta comercial com baixa transparência sobre desenho técnico interno.

## C. SDLC ampliado, operating model e adoção organizacional

12. **AWS DevOps Blog, Accelerate your Software Development Lifecycle with Amazon Q**  
    Tipo: quase primária.  
    URL: https://aws.amazon.com/blogs/devops/accelerate-your-software-development-lifecycle-with-amazon-q/  
    Uso preferencial: evidenciar cobertura do SDLC da pesquisa e planejamento até manutenção, combinando Q Business e Q Developer.  
    Limitação: demonstração guiada por exemplo, não estudo independente de impacto.

13. **AWS DevOps Blog, Adopting Amazon Q Developer in Enterprise Environments**  
    Tipo: quase primária.  
    URL: https://aws.amazon.com/blogs/devops/adopting-amazon-q-developer-in-enterprise-environments/  
    Uso preferencial: change management, patrocínio executivo, metas, aprendizado e adoção real em larga escala.  
    Limitação: mais útil para operating model de adoção do que para contratos técnicos entre agentes.

14. **Thoughtworks, AI and software delivery**  
    Tipo: síntese estratégica.  
    URL: https://www.thoughtworks.com/en-us/insights/looking-glass/looking-glass-2026/AI-and-software-delivery  
    Uso preferencial: conceito de AI-first software delivery, integração end-to-end e insistência em engineering oversight.  
    Limitação: peça analítica e prospectiva, não estudo experimental.

## D. Produtividade, evidência empírica e benchmarks

15. **GitHub Blog, Research: quantifying GitHub Copilot’s impact on developer productivity and happiness**  
    Tipo: pesquisa aplicada.  
    URL: https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/  
    Uso preferencial: produtividade multidimensional, satisfação, foco, felicidade e uso do framework SPACE.  
    Limitação: survey e pesquisa aplicada, não benchmark sistêmico de orquestração.

16. **Microsoft Research, The Impact of AI on Developer Productivity: Evidence from GitHub Copilot**  
    Tipo: pesquisa experimental.  
    URL: https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/  
    Uso preferencial: evidência causal em tarefa delimitada, útil para separar percepção de efeito medido.  
    Limitação: generaliza mal para SDLC completo ou ambientes corporativos heterogêneos.

17. **DORA Research**  
    Tipo: base institucional de pesquisa.  
    URL: https://dora.dev/research/  
    Uso preferencial: capacidades, métricas e outcomes de software delivery como sistema.  
    Limitação: não foi criado especificamente para autonomia agentic, exigindo extensão conceitual.

18. **SWE-bench**  
    Tipo: benchmark externo.  
    URL: https://www.swebench.com/  
    Uso preferencial: comparar resolução de issues reais em repositórios open source.  
    Limitação: não mede governança corporativa, compliance, handoffs interequipes ou release real.

## E. Frameworks, runtimes e building blocks para platform building

22. **OpenClaw GitHub README**  
    Tipo: primária.  
    URL: https://github.com/openclaw/openclaw  
    Uso preferencial: entender Gateway como control plane, sessões, tools, eventos, skills, canais e roteamento multiagente local-first.  
    Limitação: README de produto, muito amplo e com framing favorável.

23. **OpenClaw Docs, Gateway runbook**  
    Tipo: primária.  
    URL: https://docs.openclaw.ai/gateway  
    Uso preferencial: detalhar runtime model, boundary de autenticação, sessões, RPC, APIs compatíveis e superfícies de operação.  
    Limitação: documentação operacional, não comparação independente.

24. **Langflow Documentation, What is Langflow?**  
    Tipo: primária.  
    URL: https://docs.langflow.org/  
    Uso preferencial: mapear composition layer visual, flows, serving por API, agents e MCP.  
    Limitação: mais forte para capabilities declaradas do que para governança em larga escala.

25. **LangGraph overview**  
    Tipo: primária.  
    URL: https://docs.langchain.com/oss/python/langgraph/overview  
    Uso preferencial: runtime stateful agentic, durable execution, human-in-the-loop, memória e papel low-level de orquestração.  
    Limitação: documentação técnica do ecossistema LangChain, não benchmark comparativo.

26. **Temporal Docs, Workflows**  
    Tipo: primária.  
    URL: https://docs.temporal.io/workflows  
    Uso preferencial: sustentar workflow durável, event history, replay e resiliência operacional.  
    Limitação: fonte forte para orquestração de execução, menos específica para cognição agentic.

27. **Prefect Docs, Introduction**  
    Tipo: primária.  
    URL: https://docs.prefect.io/v3/get-started  
    Uso preferencial: state tracking, event-driven workflows, pause for approval, automations e plataforma Pythonic.  
    Limitação: posicionamento amplo, mais forte em workflow do que em handoffs multiagente complexos.

28. **OpenAI Agents SDK docs**  
    Tipo: primária.  
    URL: https://openai.github.io/openai-agents-python/  
    Uso preferencial: primitives mínimas para agents, handoffs, guardrails, sessions, MCP e tracing.  
    Limitação: ecossistema vendor-led, com risco de interpretar primitives locais como arquitetura total.

29. **AutoGen docs**  
    Tipo: primária.  
    URL: https://microsoft.github.io/autogen/stable/  
    Uso preferencial: separar AgentChat, Core e extensões; entender event-driven multi-agent runtime e MCP.  
    Limitação: a documentação mistura camadas diferentes do framework e exige leitura cuidadosa para não confundir prototipação com operação.

30. **CrewAI docs**  
    Tipo: primária.  
    URL: https://docs.crewai.com/  
    Uso preferencial: comparar agents, crews e flows com guardrails, memory, observability e console enterprise.  
    Limitação: parte importante da narrativa é comercial.

31. **Mastra docs**  
    Tipo: primária.  
    URL: https://mastra.ai/docs  
    Uso preferencial: observar o padrão moderno de framework TypeScript com Studio, templates e casos de automação de engenharia.  
    Limitação: ainda menos útil que Temporal ou Prefect para provar governança ou durabilidade de missão crítica.

32. **LangSmith docs, Tracing quickstart e Evaluation concepts**  
    Tipo: primária.  
    URLs: https://docs.langchain.com/langsmith/observability-quickstart ; https://docs.langchain.com/langsmith/evaluation-concepts  
    Uso preferencial: tracing ponta a ponta, spans, datasets, experiments, avaliação offline e online.  
    Limitação: documentação de plataforma, não comparação independente com outros stacks de observabilidade.

33. **Langfuse Overview**  
    Tipo: primária.  
    URL: https://langfuse.com/docs  
    Uso preferencial: observabilidade open source, sessões, agent graphs, avaliações e integração com OpenTelemetry.  
    Limitação: descrição de produto e benefícios, sem benchmark independente.

## F. Fontes complementares de contexto

34. **Google Cloud Blog, Google Cloud AI/ML Privacy Commitment**  
    Tipo: quase primária.  
    URL: https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-unveils-ai-and-ml-privacy-commitment  
    Uso preferencial: enquadrar a promessa de privacidade citada pelo Gemini Code Assist.  
    Limitação: compromisso corporativo amplo, não específico de software engineering.

35. **GitHub Docs, Responsible use of GitHub Copilot code review**  
    Tipo: primária.  
    URL: https://docs.github.com/en/copilot/responsible-use/code-review  
    Uso preferencial: limitações conhecidas, cautelas de uso e responsabilidade humana.  
    Limitação: documentação de safeguards, não análise independente.

36. **GitLab Duo Agent Platform overview**  
    Tipo: primária.  
    URL: https://about.gitlab.com/gitlab-duo-agent-platform/  
    Uso preferencial: contexto adicional para nomenclatura de agentes e posicionamento da plataforma.  
    Limitação: página de visão geral, menos específica que a documentação do flow.

## Lacunas ainda abertas
- mais fontes primárias de IBM, Google, AWS, Microsoft e consultorias com exemplos públicos de handoffs completos entre requisitos, arquitetura, implementação, segurança, release e operação
- estudos independentes comparando autonomia alta versus supervisão forte em ambientes corporativos
- evidência mais pública sobre como políticas e exceções são propagadas entre múltiplos agentes ao longo de um fluxo inteiro
- dados publicados sobre retrabalho, falso positivo de agentes, rollback e custo de supervisão humana

## Regras de uso desta bibliografia no restante do repositório
1. Usar fontes primárias para delimitar capacidades, guardrails e interfaces.
2. Usar pesquisa experimental e benchmarks para calibrar expectativas, não para provar maturidade ponta a ponta.
3. Tratar blogs corporativos como evidência válida de operating model publicado, mas sempre com nota de limitação.
4. Quando uma conclusão depender de múltiplas fontes, marcá-la como **inferência**, nunca como fato literal.
5. Quando uma recomendação já extrapolar o que as fontes mostram, marcá-la como **proposta conceitual** ou **recomendação de desenho futuro**.
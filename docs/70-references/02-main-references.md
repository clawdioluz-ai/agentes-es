# Referências principais

## Objetivo
Destacar a lista curta de referências mais importantes para sustentar a tese central deste repositório: orquestração ponta a ponta com IA precisa ser tratada como problema de control plane, handoffs, governança e evidência, e não apenas como geração local de código.

## Prioridade 1, fontes primárias e quase primárias mais decisivas

1. **GitHub Docs, Using GitHub Copilot code review**  
   URL: https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review  
   Por que importa: mostra com clareza o papel delimitado do agente no PR e preserva a aprovação humana fora do agente.

2. **GitHub Blog, Building an agentic memory system for GitHub Copilot**  
   URL: https://github.blog/ai-and-ml/github-copilot/building-an-agentic-memory-system-for-github-copilot/  
   Por que importa: reforça memória com citações, verificação just-in-time e contexto compartilhado como infraestrutura, não acessório.

3. **GitHub Blog, 60 million Copilot code reviews and counting**  
   URL: https://github.blog/ai-and-ml/github-copilot/60-million-copilot-code-reviews-and-counting/  
   Por que importa: oferece sinais de escala, uso de linked issues, recuperação de contexto e loops contínuos de avaliação.

4. **GitLab Docs, Software Development Flow**  
   URL: https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/  
   Por que importa: é uma das melhores fontes públicas para observar APIs, artefatos, auditabilidade e fronteiras operacionais de um fluxo estruturado.

5. **GitLab Blog, Agentic SDLC: GitLab and TCS deliver Intelligent Orchestration across the enterprise**  
   URL: https://about.gitlab.com/blog/agentic-sdlc-gitlab-and-tcs-deliver-intelligent-orchestration-across-the-enterprise/  
   Por que importa: explicita a linguagem de unified data model, multi-agent orchestration, approvals, telemetry, SBOMs e policy-aligned workflows.

6. **Atlassian, Teamwork Graph**  
   URL: https://www.atlassian.com/platform/teamwork-graph  
   Por que importa: sustenta a ideia de camada de contexto compartilhado e controles de acesso de última milha sobre superfícies conectadas de trabalho.

7. **Thoughtworks, AI and software delivery**  
   URL: https://www.thoughtworks.com/en-us/insights/looking-glass/looking-glass-2026/AI-and-software-delivery  
   Por que importa: ajuda a enquadrar o problema de ponta a ponta do software delivery com ênfase em engineering oversight.

## Prioridade 2, frameworks, runtimes e building blocks de plataforma

8. **OpenClaw GitHub README**  
   URL: https://github.com/openclaw/openclaw  
   Por que importa: mostra claramente a tese de Gateway como control plane, sessões, tools, eventos, skills e roteamento multiagente local-first.

9. **OpenClaw Docs, Gateway runbook**  
   URL: https://docs.openclaw.ai/gateway  
   Por que importa: detalha o modelo operacional do Gateway, sessões, RPC, APIs compatíveis, auth boundary e superfícies de controle.

10. **Langflow Documentation, What is Langflow?**  
   URL: https://docs.langflow.org/  
   Por que importa: bom ponto de apoio para composition layer visual, flows como workflows funcionais, serving por API e suporte a agents e MCP.

11. **LangGraph overview**  
   URL: https://docs.langchain.com/oss/python/langgraph/overview  
   Por que importa: uma das referências mais úteis para runtime stateful agentic com durable execution, human-in-the-loop e memória.

12. **Temporal Docs, Workflows**  
   URL: https://docs.temporal.io/workflows  
   Por que importa: referência forte para workflow durável, event history, replay e retomada confiável.

13. **Prefect Docs, Introduction**  
   URL: https://docs.prefect.io/v3/get-started  
   Por que importa: boa fonte para state tracking, event-driven orchestration, pause/resume e automações operacionais.

14. **OpenAI Agents SDK docs**  
   URL: https://openai.github.io/openai-agents-python/  
   Por que importa: explicita primitives mínimas úteis para handoffs, guardrails, sessions, tracing e human-in-the-loop.

15. **AutoGen docs**  
   URL: https://microsoft.github.io/autogen/stable/  
   Por que importa: ajuda a comparar frameworks multiagente mais próximos de runtime e event-driven core.

16. **CrewAI docs**  
   URL: https://docs.crewai.com/  
   Por que importa: mostra a convergência entre agents, flows, guardrails, memory, observability e enterprise console.

17. **LangSmith docs, Tracing quickstart**  
   URL: https://docs.langchain.com/langsmith/observability-quickstart  
   Por que importa: sustenta a camada de observabilidade por traces e spans, crítica para auditoria de fluxos agentic.

18. **Langfuse Overview**  
   URL: https://langfuse.com/docs  
   Por que importa: reforça observabilidade open source, agent graphs, sessões, avaliação e OpenTelemetry para reduzir lock-in.

## Prioridade 3, governança, risco e medição

19. **Google Developers, How Gemini Code Assist Standard and Enterprise use your data**  
   URL: https://developers.google.com/gemini-code-assist/docs/data-governance  
   Por que importa: reforça que governança de dados e responsabilidade operacional seguem centrais mesmo quando a IA entra no fluxo.

20. **Microsoft Learn, Security and governance - Microsoft Copilot Studio**  
   URL: https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-and-governance  
   Por que importa: acrescenta controles administrativos, políticas, logs e publicação governada como componentes estruturais.

21. **DORA Research**  
    URL: https://dora.dev/research/  
    Por que importa: fornece base sólida para pensar software delivery como sistema, não apenas como produtividade local.

22. **Microsoft Research, The Impact of AI on Developer Productivity: Evidence from GitHub Copilot**  
    URL: https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/  
    Por que importa: bom ponto de apoio para separar efeito causal em microtarefa de maturidade operacional sistêmica.

23. **SWE-bench**  
    URL: https://www.swebench.com/  
    Por que importa: benchmark útil para resolução de issues reais, com limitação explícita para governança, handoffs e operação corporativa.

## Como usar esta lista curta
### Proposta conceitual
- Começar por GitHub Docs e GitLab Docs para fronteiras operacionais e superfícies de controle.
- Usar GitHub Blog, GitLab Blog, Atlassian e Thoughtworks para operating model, contexto e direção estratégica.
- Usar OpenClaw, Langflow, LangGraph, Temporal, Prefect, OpenAI Agents SDK, AutoGen e CrewAI para mapear padrões de platform building e tradeoffs de composição.
- Usar LangSmith e Langfuse para a camada de observabilidade, avaliação e tracing de trajetórias.
- Usar Google, Microsoft, DORA e SWE-bench para calibrar governança, risco e limites de medição.
- Recorrer à bibliografia comentada completa quando a pergunta exigir nuance adicional ou triangulação mais ampla.

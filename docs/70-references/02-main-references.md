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

## Prioridade 2, governança, risco e medição

8. **Google Developers, How Gemini Code Assist Standard and Enterprise use your data**  
   URL: https://developers.google.com/gemini-code-assist/docs/data-governance  
   Por que importa: reforça que governança de dados e responsabilidade operacional seguem centrais mesmo quando a IA entra no fluxo.

9. **Microsoft Learn, Security and governance - Microsoft Copilot Studio**  
   URL: https://learn.microsoft.com/en-us/microsoft-copilot-studio/security-and-governance  
   Por que importa: acrescenta controles administrativos, políticas, logs e publicação governada como componentes estruturais.

10. **DORA Research**  
    URL: https://dora.dev/research/  
    Por que importa: fornece base sólida para pensar software delivery como sistema, não apenas como produtividade local.

11. **Microsoft Research, The Impact of AI on Developer Productivity: Evidence from GitHub Copilot**  
    URL: https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/  
    Por que importa: bom ponto de apoio para separar efeito causal em microtarefa de maturidade operacional sistêmica.

12. **SWE-bench**  
    URL: https://www.swebench.com/  
    Por que importa: benchmark útil para resolução de issues reais, com limitação explícita para governança, handoffs e operação corporativa.

## Como usar esta lista curta
### Proposta conceitual
- Começar por GitHub Docs e GitLab Docs para fronteiras operacionais e superfícies de controle.
- Usar GitHub Blog, GitLab Blog, Atlassian e Thoughtworks para operating model, contexto e direção estratégica.
- Usar Google, Microsoft, DORA e SWE-bench para calibrar governança, risco e limites de medição.
- Recorrer à bibliografia comentada completa quando a pergunta exigir nuance adicional ou triangulação mais ampla.

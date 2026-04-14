# Bibliografia e referências comentadas

## Estratégia de curadoria
Priorizar fontes primárias e materiais corporativos ou técnicos de alta credibilidade.

## Referências-chave já incorporadas

### Plataformas e fornecedores
1. **GitHub Docs, Using GitHub Copilot code review**  
   https://docs.github.com/en/copilot/how-tos/use-copilot-agents/request-a-code-review/use-code-review  
   Utilidade: mostra com precisão operacional onde o agente entra no fluxo de PR e onde o humano continua necessário.  
   Limitação: documentação de produto, não avaliação independente.

2. **GitHub Blog, 60 million Copilot code reviews and counting**  
   https://github.blog/ai-and-ml/github-copilot/60-million-copilot-code-reviews-and-counting/  
   Utilidade: traz sinais concretos sobre arquitetura agentic, memória, linked issues e métricas de feedback em produção.  
   Limitação: é relato first-party e naturalmente seleciona métricas favoráveis ao produto.

3. **GitLab Docs, Software Development Flow**  
   https://docs.gitlab.com/user/duo_agent_platform/flows/foundational_flows/software_development/  
   Utilidade: detalha APIs acessadas, modo de operação, audit log e riscos, útil para modelar contratos e governança.  
   Limitação: cobre um fluxo específico, não a totalidade do operating model empresarial.

4. **GitLab Blog, Agentic SDLC: GitLab and TCS deliver Intelligent Orchestration across the enterprise**  
   https://about.gitlab.com/blog/agentic-sdlc-gitlab-and-tcs-deliver-intelligent-orchestration-across-the-enterprise/  
   Utilidade: forte fonte para a noção de control plane, orchestration, approvals, telemetry, SBOMs e guardrails.  
   Limitação: mistura arquitetura conceitual com mensagem comercial.

5. **Atlassian Blog, Rovo Dev agent, now available in the CLI**  
   https://www.atlassian.com/blog/announcements/rovo-dev-command-line-interface  
   Utilidade: evidencia integração terminal, Jira, Confluence, Bitbucket, memória e uso de benchmark externo.  
   Limitação: foco promocional em capacidade do produto.

6. **Atlassian, Teamwork Graph**  
   https://www.atlassian.com/platform/teamwork-graph  
   Utilidade: referência importante para camada de contexto compartilhado e controles de acesso contextuais.  
   Limitação: descreve princípios de plataforma, mas não métricas detalhadas de resultados em SDLC.

### Pesquisa, produtividade e benchmarking
7. **GitHub Blog, Research: quantifying GitHub Copilot’s impact on developer productivity and happiness**  
   https://github.blog/news-insights/research/research-quantifying-github-copilots-impact-on-developer-productivity-and-happiness/  
   Utilidade: importante para discutir produtividade como fenômeno multidimensional e alinhado ao framework SPACE.  
   Limitação: survey e pesquisa aplicada ao ecossistema GitHub, não benchmark de orquestração fim a fim.

8. **Microsoft Research, The Impact of AI on Developer Productivity: Evidence from GitHub Copilot**  
   https://www.microsoft.com/en-us/research/publication/the-impact-of-ai-on-developer-productivity-evidence-from-github-copilot/  
   Utilidade: experimento controlado com evidência causal mais forte que materiais puramente observacionais.  
   Limitação: tarefa única, ambiente controlado e foco em implementação.

9. **DORA Research**  
   https://dora.dev/research/  
   Utilidade: base sólida para pensar capacidades, métricas e outcomes de software delivery como sistema.  
   Limitação: não foi desenhado especificamente para agentes ou autonomia multi-etapa.

10. **SWE-bench**  
    https://www.swebench.com/  
    Utilidade: benchmark externo relevante para comparar agentes de software engineering em resolução de issues reais.  
    Limitação: não captura governança corporativa, compliance ou handoffs organizacionais.

### Síntese estratégica
11. **Thoughtworks, AI and software delivery**  
    https://www.thoughtworks.com/en-us/insights/looking-glass/looking-glass-2026/AI-and-software-delivery  
    Utilidade: boa fonte para a tese de AI-first software delivery com forte engineering oversight.  
    Limitação: é síntese prospectiva, não estudo experimental.

## Lacunas ainda abertas
- mais fontes primárias de Google, AWS, Microsoft e consultorias top-tier sobre operating model fim a fim
- evidência pública mais detalhada sobre handoffs entre requisitos, arquitetura, implementação, segurança, release e operação
- estudos independentes sobre trade-off entre autonomia, retrabalho e governança

## Notas
As referências acima já sustentam a primeira versão robusta do corpus. A expansão futura deve priorizar novos materiais que aumentem diversidade de fonte e profundidade em governança, plataforma e métricas.
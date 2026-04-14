# ADR-006, evidência e auditabilidade como preocupações de primeira classe

- Status: aceito
- Data: 2026-04-14

## Contexto
O repositório diferencia explicitamente fato, inferência e proposta. A mesma disciplina precisa aparecer na própria plataforma, porque outputs sem trilha de decisão, proveniência e contexto verificável são frágeis para operação séria.

## Decisão
A plataforma tratará **evidence and auditability** como capacidades centrais do produto e da arquitetura.

Toda decisão material, handoff relevante, approval, exceção ou saída significativa deve poder ser ligada a contexto, justificativa e evidência rastreável.

## Racional
Sem evidência, a plataforma pode até gerar velocidade local, mas não sustenta confiança, aprendizado comparativo, governança nem melhoria contínua.

## Consequências
### Positivas
- Melhora explicabilidade operacional.
- Permite auditoria, benchmarking interno e revisão pós-fato.
- Reforça qualidade de governança e aprendizado de sistema.
- Distingue trace técnico de evidência decisória.

### Tradeoffs
- Exige modelagem e retenção mais intencionais.
- Pode aumentar custo de instrumentação e disciplina de registro.
- Impõe cuidado extra com sensibilidade, retenção e proveniência dos dados.

## Implicações para a próxima fase
- Evidence deve aparecer como objeto de domínio, não só como log disperso.
- Observabilidade deve cobrir trajetória do trabalho, não apenas outputs finais.
- Ausência de evidência suficiente deve ser tratada como sinal de risco ou incompletude.

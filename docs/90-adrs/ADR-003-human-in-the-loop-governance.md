# ADR-003, governança human-in-the-loop como primitive

- Status: aceito
- Data: 2026-04-14

## Contexto
A pesquisa mostra que supervisão humana não é exceção processual, mas requisito recorrente em fluxos materiais de software delivery, especialmente quando risco, impacto, irreversibilidade ou ambiguidade aumentam.

## Decisão
A plataforma tratará **human-in-the-loop governance** como primitive de arquitetura e produto, não como camada cosmética adicionada depois.

Aprovação, revisão, escalonamento, pausa, redirecionamento, rejeição e aceitação de risco residual devem existir como capacidades nativas.

## Racional
A autonomia útil precisa ser graduada por risco e reversibilidade. Portanto, a plataforma deve explicitar onde a automação pode seguir sozinha, onde precisa de supervisão condicional e onde a autorização humana é mandatória.

## Consequências
### Positivas
- Reduz risco de automação opaca em etapas críticas.
- Favorece segregação de funções e accountability.
- Torna a confiança operacional mais realista e sustentável.
- Aproxima o produto de exigências corporativas reais.

### Tradeoffs
- Reduz a narrativa de autonomia total.
- Introduz mais estados, filas e superfícies operacionais.
- Exige desenho cuidadoso para não transformar governança em atrito excessivo.

## Implicações para a próxima fase
- Toda arquitetura deve suportar checkpoints humanos explícitos.
- Policies devem ser orientadas a risco e reversibilidade.
- O mesmo especialista não deve concentrar planejamento, execução, validação e aprovação final em etapas críticas sem contrapeso externo.

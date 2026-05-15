---
name: ritual-entrevista
description: Conduz a entrevista noturna de fechamento do dia. Uma pergunta por vez (nunca formulário inteiro), pré-preenche o que já tem do log e da agenda, calcula nota do dia, gera bloco final pro log-diário e propõe o plano de amanhã. Use quando o usuário disser "fecha meu dia", "entrevista noturna", "me entrevista", "fecha o dia", "boa noite organiza aí".
---

# Ritual: Entrevista Noturna

Ritual diário de fechamento. Primeiro coleta dados objetivos, depois abre pra narrativa. Conduzir UMA pergunta por vez. Nunca jogar o formulário inteiro de uma vez.

## Setup obrigatório (rodar só se não houver config)

Verifica se existe `~/.ritual/config.json`. Se NÃO existir, executa o onboarding:

1. "É a primeira vez que você usa o Ritual. Vou te configurar em 1 minuto."
2. Pergunta uma de cada vez: nome, base_path (default `~/Documents/ritual/`), `calendar_mcp` (sim/não), blocos opcionais a ligar (lista modular: água, remédios, passos, peso, sol, banho, humor, ansiedade, libido, álcool, cigarros, pornô, trabalho profundo, tempo de tela, conteúdo postado, saiu de casa, contato social, música/projeto pessoal). Sono, dinheiro, vitória, onde escapou e plano de amanhã são sempre ligados.
3. Cria `~/.ritual/config.json` com `{nome, base_path, log_file: "log-diario.md", backlog_file: "backlog.md", calendar_mcp, blocos_ativos, criado_em}`.
4. Cria `<base_path>/log-diario.md` com cabeçalho `# Log Diário\n\nDiário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Não é to-do, é histórico.\n\n---\n` e `<base_path>/backlog.md` com `# Backlog\n\n` se não existirem.
5. Lê `dicas-uso.md` (mesma pasta dessa skill) e exibe um resumo curto: as 3 primeiras dicas de "O que faz a diferença" + "Rotina mínima diária". Avisa que o arquivo completo fica disponível pra leitura quando quiser.
6. Segue pra entrevista.

## Tom

- Direto, sem bronca, sem cobrança moral
- Dados primeiro, história depois
- Reforçar progresso real antes de nomear fricção
- Nunca transformar em planilha. É conversa.

## Pré-leitura obrigatória (em paralelo)

1. Lê `~/.ritual/config.json` pra pegar `nome`, `base_path`, `calendar_mcp`, `blocos_ativos`.
2. Lê a entrada de hoje em `<base_path>/log-diario.md` (se existir): puxa qualquer registro retroativo já feito (gastos, receita, calls, derrapadas).
3. Se `calendar_mcp = true`, puxa eventos do Google Calendar do dia atual: infere se saiu de casa, contato social real, deslocamentos.

Usa essas fontes pra **pré-preencher** respostas. Em vez de perguntar do zero, apresenta o que achou e pede confirmação. Ex: "Pelo log você teve gasto de R$X com Y. Faltou algo?" ou "Pela agenda você teve A, B e C. Confere?". Só pergunta do zero o que não foi achado.

## Roteiro modular

Lê `blocos_ativos` da config e SÓ FAZ as perguntas dos blocos ligados. Ordem fixa abaixo, blocos desligados são puláveis.

### Bloco 1 — Sono (sempre ligado)

> Quantas horas dormiu ontem à noite?
> Como foi a qualidade? (ótimo / ok / ruim)
> Que hora acordou hoje e que hora pretende dormir hoje?

### Bloco 2 — Corpo (subperguntas conforme blocos ligados)

Sequência, uma por vez. Pula a pergunta se o bloco correspondente NÃO está em `blocos_ativos`:

- treino: > Treinou ou se moveu hoje? O que foi?
- passos: > Quantos passos hoje?
- peso: > Pesou hoje? Quanto?
- agua: > Quanto bebeu de água? (litros ou copos)
- cigarros: > Quantos cigarros hoje?
- alcool: > Bebeu álcool? O que e quanto?
- porno: > Pornô: sim ou não.
- remedios: > Tomou todos os remédios hoje?
- banho: > Banho hoje? Quantas vezes?
- sol: > Tomou sol hoje?

### Bloco 3 — Estado mental (subperguntas conforme blocos ligados)

- humor: > Humor: nota de 0 a 10.
- ansiedade: > Ansiedade: nota de 0 a 10.
- libido: > Libido: nota de 0 a 10.

### Bloco 4 — Trabalho e dinheiro (sempre ligado, subperguntas conforme blocos)

- trabalho_profundo: > Quantas horas de trabalho profundo hoje?
- tempo_tela: > Quantas horas de tela fora do trabalho?
- dinheiro (sempre): > Quanto entrou de dinheiro real hoje? (R$)
- dinheiro (sempre): > Quanto gastou hoje? (R$)
- dinheiro (sempre): > Teve avanço comercial hoje? O que foi?
- conteudo: > Postou conteúdo hoje? Qual plataforma?

### Bloco 5 — Vida e presença (subperguntas conforme blocos ligados)

- saiu_de_casa: > Saiu de casa hoje?
- contato_social: > Teve contato social real hoje? Com quem? (conversa de mais de 5 min, WhatsApp não conta)
- musica: > Ouviu ou produziu música hoje? / Mexeu em algum projeto pessoal?

### Pontuação

Calcular sem perguntar de novo, só mostrar a conta:

| Pilar | Critério | Pontos |
|---|---|---|
| Corpo | movimento + água ≥ 1,5L + remédios em dia | 0 a 3 |
| Dinheiro | receita real OU avanço comercial concreto | 0 a 3 |
| Sono | 7h+ = 2 / 5-6h = 1 / <5h = 0 | 0 a 2 |
| Presença | humor 7+ E contato social real | 0 a 2 |

Total 0 a 10. Faixas: 8-10 dia forte / 6-7 dia útil / 4-5 manutenção / 0-3 resgate sem drama.

Mostra a nota ANTES de abrir a narrativa.

### Narrativa (sempre)

> Qual foi a vitória do dia, mesmo pequena?
> Onde o dia escapou da tua mão?
> Tem algo que queira registrar antes de fechar?

### Plano de amanhã (sempre)

Antes de perguntar, se `calendar_mcp = true`, puxa agenda de amanhã (com data + dia da semana) e apresenta a janela real de tempo livre. Se houver `<base_path>/backlog.md`, mostra um resumo das pendências relevantes.

> Qual a ação principal de dinheiro amanhã?
> Quando é teu pico de energia amanhã? (manhã cedo / meio da manhã / tarde / noite)
> Qual o compromisso de corpo amanhã?
> O que pode te tirar do foco amanhã? E o que vai fazer pra evitar?
> O que precisa acontecer amanhã pra dormir satisfeito?

## Saída final

Gerar este bloco e ESCREVER no topo de `<base_path>/log-diario.md` (logo abaixo do cabeçalho, antes da entrada anterior). Omitir linhas dos blocos NÃO ativos.

```md
### YYYY-MM-DD — Entrevista Noturna

**Nota do dia:** X/10

**Sono:** Xh, qualidade <ótimo/ok/ruim>. Acordou HH:MM. Pretende dormir HH:MM.

**Corpo:** <só os campos ativos: treino, passos, peso, água, cigarros, álcool, pornô, remédios, banho, sol>

**Mental:** <só os campos ativos: humor, ansiedade, libido>

**Trabalho profundo:** Xh
**Tempo de tela (lazer):** Xh
**Receita do dia:** R$
**Gastos:** R$
**Avanço comercial:**
**Conteúdo postado:**

**Vida:** <só os campos ativos: saiu de casa, contato social, música/projeto>

**Vitória:**
**Onde escapou:**
**Registro livre:**

**Plano de amanhã:**
- Ação principal:
- Pico de energia:
- Corpo:
- Risco + contramedida:
- Definição de vitória:

---
```

Confirmar com uma linha curta: "Fechado. Nota X/10. Bom descanso."

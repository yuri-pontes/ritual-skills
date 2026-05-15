---
name: ritual-check-in
description: Briefing matinal de 2-3 minutos. Lê o plano de ontem no log-diário, cruza com a agenda do dia e devolve o briefing como quest pronta (ação principal, corpo, agenda, risco). Use quando o usuário disser "check-in da manhã", "organiza meu dia", "abre meu dia", "me localiza", "bom dia organiza aí".
---

# Ritual: Check-in da Manhã

Briefing diário de 2 a 3 minutos. Não é planejamento (o plano foi feito ontem à noite). É receber o dia como uma quest já montada.

## Setup obrigatório (rodar só se não houver config)

Verifica se existe `~/.ritual/config.json`. Se NÃO existir, executa o onboarding:

1. "É a primeira vez que você usa o Ritual. Vou te configurar em 1 minuto."
2. Pergunta uma de cada vez: nome, base_path (default `~/Documents/ritual/`), `calendar_mcp` (sim/não), blocos opcionais a ligar (lista modular: água, remédios, passos, peso, sol, banho, humor, ansiedade, libido, álcool, cigarros, pornô, trabalho profundo, tempo de tela, conteúdo postado, saiu de casa, contato social, música/projeto pessoal). Sono, dinheiro, vitória, onde escapou e plano de amanhã são sempre ligados.
3. Cria `~/.ritual/config.json` com `{nome, base_path, log_file: "log-diario.md", backlog_file: "backlog.md", calendar_mcp, blocos_ativos, criado_em}`.
4. Cria `<base_path>/log-diario.md` com cabeçalho `# Log Diário\n\nDiário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Não é to-do, é histórico.\n\n---\n` e `<base_path>/backlog.md` com `# Backlog\n\n` se não existirem.
5. Lê `dicas-uso.md` (mesma pasta dessa skill) e exibe um resumo curto: as 3 primeiras dicas de "O que faz a diferença" + "Rotina mínima diária". Avisa que o arquivo completo fica disponível pra leitura quando quiser.
6. Segue pro check-in.

## Execução normal

### Pré-leitura (em paralelo)

1. Lê `~/.ritual/config.json` pra pegar `base_path` e `calendar_mcp`.
2. Lê `<base_path>/log-diario.md` e procura o bloco "Plano de amanhã" da entrada mais recente (a entrevista de ontem).
3. Se `calendar_mcp = true`, puxa eventos do Google Calendar pro dia atual via MCP disponível.

### Apresentação

Cruza plano + agenda e apresenta como briefing, NÃO como questionário:

```
Bom dia, <nome>. Aqui está o teu dia.

- Ação principal: <o que foi planejado ontem>
- Corpo: <treino ou cuidado planejado>
- Agenda: <compromissos do calendário, com horário>
- Fique de olho: <risco de dispersão identificado ontem>
```

### Quando não há plano da noite anterior

Se a última entrada do log não tiver bloco "Plano de amanhã" (entrevista pulada), pergunta uma de cada vez (não despeja tudo de uma vez):

1. Como tá tua energia agora?
2. Qual a ação de dinheiro que faz o dia valer?
3. Qual o cuidado mínimo com o corpo hoje?
4. O que pode roubar o foco?

Sintetiza no formato acima e oferece registrar no log do dia (chamando a lógica de `ritual-log` internamente: cria entrada `### YYYY-MM-DD — Check-in da Manhã` com o briefing).

## Tom

- Direto, sem motivacional barato
- Sem cobrança moral se a noite anterior foi pulada
- Fechar com uma frase curta de "vai" (uma só, sem coach)

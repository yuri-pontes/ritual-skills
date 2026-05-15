---
name: ritual-backlog
description: Varre as últimas entradas do log-diário, extrai pendências e follow-ups que vazaram nos registros (próximos passos de calls, decisões pendentes, "preciso voltar nisso") e propõe entradas pro backlog.md. O log fica intocado, o backlog é a vista derivada do que precisa virar ação. Use quando o usuário disser "atualiza o backlog", "extrai backlog do log", "ritual de backlog", "puxa pendências do log", ou no review semanal.
---

# Ritual: Backlog

Vista derivada do log. O log captura a vida acontecendo, e muita coisa que aparece lá vira tarefa. Sem extração periódica, vira histórico morto.

## Setup obrigatório (rodar só se não houver config)

Verifica se existe `~/.ritual/config.json`. Se NÃO existir, executa o onboarding:

1. "É a primeira vez que você usa o Ritual. Vou te configurar em 1 minuto."
2. Pergunta uma de cada vez: nome, base_path (default `~/Documents/ritual/`), `calendar_mcp` (sim/não), blocos opcionais a ligar (lista modular: água, remédios, passos, peso, sol, banho, humor, ansiedade, libido, álcool, cigarros, pornô, trabalho profundo, tempo de tela, conteúdo postado, saiu de casa, contato social, música/projeto pessoal). Sono, dinheiro, vitória, onde escapou e plano de amanhã são sempre ligados.
3. Cria `~/.ritual/config.json` com `{nome, base_path, log_file: "log-diario.md", backlog_file: "backlog.md", calendar_mcp, blocos_ativos, criado_em}`.
4. Cria `<base_path>/log-diario.md` com cabeçalho `# Log Diário\n\nDiário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Não é to-do, é histórico.\n\n---\n` e `<base_path>/backlog.md` com `# Backlog\n\n` se não existirem.
5. Lê `dicas-uso.md` (mesma pasta dessa skill) e exibe um resumo curto: as 3 primeiras dicas de "O que faz a diferença" + "Rotina mínima diária". Avisa que o arquivo completo fica disponível pra leitura quando quiser.
6. Segue pro ritual de backlog.

## Execução

### 1. Pré-leitura

1. Lê `~/.ritual/config.json` pra pegar `base_path`, `log_file`, `backlog_file`.
2. Lê `<base_path>/<log_file>` inteiro (ou últimos 30 dias se for muito grande).
3. Lê `<base_path>/<backlog_file>` pra saber o que já está lá.

### 2. Pergunta de escopo

> Quer extrair de quanto tempo? (últimos 7 dias / últimos 30 dias / desde o último ritual de backlog / tudo)

Default: últimos 7 dias.

### 3. Extração

Varre as entradas do log no escopo escolhido e identifica candidatos a backlog. Padrões a procurar:

- Verbos de intenção: "preciso", "vou", "tenho que", "falta", "ainda devo", "voltar nisso", "lembrar de"
- Próximos passos de calls/reuniões: "combinado: X", "ficou de me mandar Y", "vou ligar pro Z"
- Decisões pendentes: "decidir entre", "definir até", "esperando resposta de"
- Compromissos verbais: "prometi", "disse que faria"
- Bloqueios mencionados: "travado em", "depende de"

Pra cada candidato, monta:
- **Tarefa** (verbo no infinitivo, direto): "Ligar pro João sobre proposta"
- **Origem**: data da entrada do log de onde saiu
- **Prazo** (se mencionado): senão, em branco
- **Categoria** (se óbvio pelo contexto): trabalho / pessoal / saúde / projeto X

### 4. Apresentação

Mostra a lista de candidatos numerada, agrupada por categoria quando claro. Pra cada um:

```
[N] <Tarefa> (origem: log de YYYY-MM-DD)
    <prazo se houver>
```

Pergunta no fim:
> Quais entram no backlog? (ex: "todas", "1 3 5", "só as de trabalho", "nenhuma")
> Quer editar alguma antes de salvar? (n/edita o número)

### 5. Escrita

Pega as aprovadas e adiciona em `<base_path>/<backlog_file>` agrupadas por categoria. Formato:

```md
## <Categoria>

- [ ] <Tarefa> _<origem: YYYY-MM-DD>_ <prazo se houver>
```

Não duplica: se a tarefa já existe (match aproximado por palavras-chave), pula e avisa.

Não toca no log-diário. O log permanece intocado.

### 6. Confirmação

Linha curta: "Adicionei N tarefas no backlog. M já estavam lá, puladas."

## Regras

- Não inventar tarefas que não estão no log
- Não traduzir registro casual em obrigação ("escapei e comi besteira" NÃO vira "comer melhor")
- Se a entrada do log já indica que a coisa foi resolvida ("liguei pro João, fechado"), não puxar
- Conservador: melhor sub-extrair do que poluir o backlog
- Quando em dúvida sobre categoria, deixa em "geral"

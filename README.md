# Ritual

Pacote de skills de produtividade pessoal pro Claude Code. Quatro rituais de baixa fricção pra organizar o dia, manter histórico, extrair pendências e fechar a noite com a cabeça leve.

## Os 4 rituais

1. **`/ritual-check-in`** (manhã, 2-3 min)
   Lê o plano de ontem + agenda + log e devolve o briefing do dia em formato de quest pronta. Não é planejamento, é recepção do dia.

2. **`/ritual-log`** (durante o dia, 10 segundos)
   Registro ao vivo. Termina uma call, fecha um deal, derrapa em algo? Fala "registra no log: <frase solta>". O Claude infere o contexto e encaixa no lugar certo.

3. **`/ritual-entrevista`** (noite, 5-10 min)
   Conduz uma entrevista uma pergunta por vez (não joga formulário na cara), sintetiza no formato de log, calcula a nota do dia e propõe o gancho de amanhã.

4. **`/ritual-backlog`** (semanal ou quando o log inflar)
   Varre as últimas entradas do log, identifica follow-ups e próximos passos que vazaram nos registros, e propõe entradas pro `backlog.md`. O log fica intocado, o backlog vira a vista derivada do que precisa virar ação.

O log cresce do mais recente pro mais antigo. Topo = hoje.

## Instalação

1. Copia as 4 pastas de skill pra dentro de `~/.claude/skills/` (uso global em qualquer projeto) ou `<seu-projeto>/.claude/skills/` (uso só naquele projeto):

```bash
cp -r ritual/ritual-check-in ritual/ritual-log ritual/ritual-entrevista ritual/ritual-backlog ~/.claude/skills/
```

2. Roda qualquer um dos rituais pela primeira vez. O Claude detecta que não tem config e te conduz no setup (~1 minuto). Pergunta:
   - Teu nome
   - Onde guardar os arquivos (default `~/Documents/ritual/`)
   - Que blocos da entrevista noturna ligar (corpo, dinheiro, hábitos, etc, modular)
   - Se tem Google Calendar conectado via MCP

3. Pronto. A config fica em `~/.ritual/config.json` e os arquivos em `<base_path>/log-diario.md` e `<base_path>/backlog.md`.

## Filosofia

- **Histórico, não to-do.** O log é diário de bordo. O backlog é to-do. Não misturar.
- **Uma pergunta por vez.** Entrevista é conversa, não formulário.
- **Honestidade > marketing pessoal.** O campo "onde escapou" é o mais importante. Sem ele, o log vira propaganda.
- **Ao vivo > de memória.** Registrar na hora evita que o cérebro reescreva a história à noite.

## Customização

Os blocos da entrevista são modulares. No setup você liga só o que faz sentido pra você (pode ignorar tracking de cigarro, álcool, libido, peso, passos, etc). Pra mexer depois, edita `~/.ritual/config.json` direto.

Pra mudar o tom das skills (mais seco, mais terapêutico, mais militar), edita os `SKILL.md` dentro da pasta de cada uma. São arquivos curtos.

## Crédito

Sistema desenhado pelo Yuri Pontes em maio/2026. Empacotado pra comunidade depois de seis meses rodando como prática diária pessoal.

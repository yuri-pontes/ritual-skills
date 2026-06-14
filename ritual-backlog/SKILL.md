---
name: ritual-backlog
description: Varre as últimas entradas do log-diário, extrai pendências e follow-ups que vazaram nos registros (próximos passos de calls, decisões pendentes, "preciso voltar nisso") e propõe entradas pro backlog.md. O log fica intocado, o backlog é a vista derivada do que precisa virar ação. Use quando o usuário disser "atualiza o backlog", "extrai backlog do log", "ritual de backlog", "puxa pendências do log", ou no review semanal.
---

# Ritual: Backlog

Vista derivada do log. O log captura a vida acontecendo, e muita coisa que aparece lá vira tarefa. Sem extração periódica, vira histórico morto. Roda uma vez por semana.

## Setup (só na primeira vez: se não houver `~/.ritual/config.json`)

Se a config existir, pular pra execução. Se NÃO existir, conduzir o onboarding, uma pergunta por vez:

1. "Primeira vez aqui. Vou te configurar em 1 minuto: depois é só rodar." Pergunta o nome.
2. Onde guardar os arquivos? (default `~/Documents/ritual/`, aceita caminho absoluto)
3. **Quais áreas da vida você quer destravar ou acompanhar agora?** Lista abaixo, **recomenda começar com 1 ou 2**:
   - 🫀 Saúde física → treino, passos, peso, água, sol
   - 🧠 Saúde mental → humor, ansiedade, libido
   - 💰 Trabalho & dinheiro → trabalho profundo, tempo de tela, receita, gasto, avanço comercial
   - 🤝 Relações & presença → saiu de casa, contato social real
   - 🚭 Vícios & escapes → cigarro, álcool, pornô
   - 🎯 Projeto pessoal → a pessoa nomeia (instrumento, escrita, esporte, estudo, o que for)
4. Dentro de cada área, confirma quais métricas ligar.
5. (Se ligou Projeto pessoal) Qual prática quer manter no radar? Nome livre.
6. Tem Google Calendar conectado via MCP? (sim/não, default não).
7. (Opcional) Usa gravador de call conectado? (sim/não, default não).
8. Grava `~/.ritual/config.json` (schema em `config.exemplo.json` na raiz) e cria `<base_path>/log-diario.md` e `<base_path>/backlog.md` com `# Backlog\n\n`, se não existirem.
9. Mostra um resumo curto de uso e segue pro ritual de backlog.

## Execução

### 1. Pré-leitura

1. Lê `~/.ritual/config.json` (`base_path`, `log_file`, `backlog_file`).
2. Lê `<base_path>/<log_file>` (ou os últimos 30 dias, se for muito grande).
3. Lê `<base_path>/<backlog_file>` pra saber o que já está lá.

### 2. Escopo

> De quanto tempo quer extrair? (últimos 7 dias / últimos 30 dias / desde o último backlog / tudo)

Default: últimos 7 dias.

### 3. Extração

Varre as entradas do log no escopo e identifica candidatos a tarefa. Padrões:

- Verbos de intenção: "preciso", "vou", "tenho que", "falta", "voltar nisso", "lembrar de".
- Próximos passos de calls: "combinado: X", "ficou de me mandar Y", "vou ligar pro Z".
- Decisões pendentes: "decidir entre", "definir até", "esperando resposta de".
- Compromissos verbais: "prometi", "disse que faria".
- Bloqueios: "travado em", "depende de".

Pra cada candidato: **tarefa** (verbo no infinitivo), **origem** (data do log), **prazo** (se mencionado), **categoria** (se óbvia pelo contexto).

### 4. Apresentação

Lista numerada, agrupada por categoria quando claro:

```
[N] <Tarefa> (origem: log de YYYY-MM-DD): <prazo se houver>
```

Fecha com:
> Quais entram? (ex: "todas", "1 3 5", "só as de trabalho", "nenhuma") · Quer editar alguma antes?

### 5. Escrita

Adiciona as aprovadas em `<base_path>/<backlog_file>`, agrupadas por categoria:

```md
## <Categoria>

- [ ] <Tarefa> _<origem: YYYY-MM-DD>_ <prazo se houver>
```

Não duplica (match aproximado por palavra-chave): se já existe, pula e avisa. Não toca no log.

### 6. Confirmação

"Adicionei N tarefas. M já estavam lá, puladas."

## Regras

- Não inventar tarefa que não está no log.
- Não traduzir registro casual em obrigação ("comi besteira" NÃO vira "comer melhor").
- Se o log já indica resolução ("liguei pro João, fechado"), não puxar.
- Conservador: melhor sub-extrair do que poluir o backlog.
- Em dúvida sobre categoria, "geral".

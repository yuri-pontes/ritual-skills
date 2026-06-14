# Ritual

Sistema de **tracking pessoal + rituais de início e fim de dia** pro Claude Code. Você acompanha as métricas da sua vida (sono, treino, trabalho profundo, humor, dinheiro, escapadas, o que escolher), fecha o dia em conversa, abre o dia já organizado — e o histórico vira base pra você enxergar padrões e decidir com dado, não com memória.

Baixa fricção: uma pergunta por vez, pré-preenchimento do que dá pra inferir, e você só liga o que de fato quer acompanhar.

## Como funciona

Cinco rituais. Você não usa todos todo dia — o núcleo diário são três (check-in, log, entrevista):

1. **`/ritual-check-in`** (manhã, ~2-3 min)
   Registra seu sono (memória mais fresca de manhã) e devolve o dia montado: a ação principal que você planejou ontem + a agenda de hoje. Não é planejamento, é recepção.

2. **`/ritual-log`** (durante o dia, ~10 s)
   Registro ao vivo. "Registra no log: fechei a call com o João, toparam o orçamento." O Claude encaixa no lugar certo, com campo padronizado. Cru funciona melhor que caprichado.

3. **`/ritual-entrevista`** (noite, ~5-10 min)
   Fecha o dia em conversa. Antes de começar, te devolve um resumo do que rolou (gatilho de memória) e resgata o que você fez mas esqueceu de anotar. Pergunta só as métricas das áreas que você ligou, calcula a nota do dia e monta o plano de amanhã (que vira o gancho do check-in).

4. **`/ritual-backlog`** (semanal, ou quando o log inflar)
   Varre o log, encontra os follow-ups e próximos passos que vazaram nos registros, e propõe tarefas pro `backlog.md`. O log fica intocado — ele é histórico, o backlog é to-do.

5. **`/ritual-analise`** (sob demanda)
   Lê o histórico e devolve tendências: média de sono, dias fortes vs. dias de resgate, correlações ("energia despenca quando você dorme menos de 6h"), onde você mais escapa. É aqui que o tracking vira decisão.

O log cresce do mais recente pro mais antigo. Topo = hoje.

## Instalação

Cola no terminal (instala global, funciona em qualquer projeto):

```bash
mkdir -p ~/.claude/skills && cd ~/.claude/skills && git clone https://github.com/yuri-pontes/ritual-skills.git _ritual-tmp && mv _ritual-tmp/ritual-* . && rm -rf _ritual-tmp
```

Pra instalar só num projeto, troca `~/.claude/skills` por `<seu-projeto>/.claude/skills`.

Depois roda **qualquer** um dos rituais pela primeira vez. Não tem config? O Claude detecta e te conduz no setup (~1 min), uma pergunta por vez.

## Setup — personalização por áreas da vida

O setup não te entrega uma planilha de 30 campos. Ele pergunta **quais áreas da vida você quer destravar ou acompanhar agora** e liga só as métricas dessas áreas:

| Área | Métricas |
|---|---|
| 🫀 Saúde física | treino, passos, peso, água, sol |
| 🧠 Saúde mental | humor, ansiedade, libido |
| 💰 Trabalho & dinheiro | trabalho profundo, tempo de tela, receita, gasto, avanço |
| 🤝 Relações & presença | saiu de casa, contato social real |
| 🚭 Vícios & escapes | cigarro, álcool, pornô (o "onde escapou") |
| 🎯 Projeto pessoal | você nomeia (instrumento, escrita, esporte, estudo, o que for) |

**Comece com 1 ou 2 áreas.** Ligar mais depois é fácil. Área que você abandona em três dias mata o ritual inteiro.

Independente das áreas, o **núcleo** está sempre ligado: sono, vitória do dia, onde escapou, plano de amanhã e a nota do dia. É o esqueleto do ritual.

A config fica em `~/.ritual/config.json` (schema em [`config.exemplo.json`](config.exemplo.json)). Os dados ficam em `<base_path>/log-diario.md` e `<base_path>/backlog.md`. Pra mexer depois, edita a config direto.

### Integrações (opcionais)

O ritual funciona 100% em markdown puro, sem nenhuma conta conectada. Se você tiver, liga no setup:

- **Google Calendar (via MCP):** pré-preenche a agenda no check-in e na entrevista.
- **Gravador de call (Fathom, Otter, etc):** no fim do dia, cruza o que foi decidido nas calls com o que você registrou e resgata o que faltou.

Sem integração nenhuma, o "resgate" do fim do dia continua funcionando — vira a pergunta "o que você fez hoje que não anotou?" + a leitura da agenda, se tiver.

## Formato dos dados (por que importa)

As métricas são gravadas com **campo e unidade fixos** (`**Sono:** 7.5h`, `**Água:** 2L`, `**Trabalho profundo:** 4h`), sempre no mesmo formato. Não é firula: é o que permite o `/ritual-analise` ler meses de histórico e calcular tendências. Diário em prosa solta não é analisável — esse aqui é.

## Filosofia

- **Tracking que soma, não que cobra.** O ritual existe pra te ajudar a se organizar e se conhecer, não pra virar mais uma planilha que te culpa.
- **Histórico, não to-do.** O log é diário de bordo. O backlog é to-do. Não misturar.
- **Uma pergunta por vez.** Ritual é conversa, não formulário.
- **Honestidade > marketing pessoal.** O campo "onde escapou" é o mais importante. Sem ele, o log vira propaganda.
- **Ao vivo > de memória.** Registrar na hora evita que o cérebro reescreva a história à noite.
- **Comece pequeno.** Poucas áreas, bem acompanhadas, valem mais que muitas abandonadas.

## Customização

Tudo é editável na config (`~/.ritual/config.json`): ligar/desligar áreas e métricas, renomear o projeto pessoal, ativar integrações. Pra mudar o tom das skills (mais seco, mais terapêutico, mais direto), edita o `SKILL.md` de cada uma — são curtos.

## Funciona? Um mês de uso real

Antes de empacotar, rodei isso por um mês: **check-in em 30 dias diferentes, entrevista em 28**, sequência de 13 dias sem furar, nota média ~7,8. Mais importante que os números: a rede de captura parou de deixar cobrança, prazo e gasto caírem no vão, e o histórico me mostrou padrões sobre mim que eu sentia mas não via.

O relato completo, com os casos reais (anonimizados) e a parte honesta do que **não** funcionou de primeira, está em [`CASE-STUDY.md`](CASE-STUDY.md).

## Crédito

Sistema desenhado por Yuri Pontes, a partir de uma prática diária pessoal, e empacotado pra qualquer pessoa que queira se organizar e acompanhar a própria vida com método.

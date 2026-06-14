# Ritual

Um sistema de organização pessoal pro Claude Code. Você acompanha o que importa na sua rotina (sono, treino, trabalho, humor, dinheiro, o que você escolher), fecha o dia conversando com o Claude e abre o dia já organizado. Com o tempo, o histórico te mostra o que tá funcionando na sua vida e o que tá te derrubando.

A ideia é ter o mínimo de fricção possível. Uma pergunta por vez, o Claude já adianta o que dá pra adivinhar, e você liga só o que de fato quer acompanhar.

## Os cinco rituais

Três você usa todo dia, dois de vez em quando.

- **`/ritual-check-in`** (manhã, uns 3 min): registra seu sono e te entrega o dia montado, com a ação principal que você deixou planejada na noite anterior e a agenda de hoje.
- **`/ritual-log`** (durante o dia, 10 segundos): "registra no log: fechei a call, toparam o orçamento". O Claude guarda no lugar certo. Quanto mais cru você joga, melhor.
- **`/ritual-entrevista`** (noite, uns 5 a 10 min): fecha o dia conversando. Antes de começar ele te resume o que rolou e resgata o que você fez e esqueceu de anotar. Pergunta só as coisas das áreas que você ligou, calcula a nota do dia e já deixa o plano de amanhã pronto.
- **`/ritual-backlog`** (uma vez por semana): lê o log e puxa os follow-ups e próximos passos que vazaram nos registros pro seu backlog.
- **`/ritual-analise`** (quando você quiser): lê o histórico e te mostra as tendências. Média de sono, dias bons e dias ruins, onde você mais escapa, o que costuma andar junto com seus dias melhores.

O log cresce de cima pra baixo, hoje sempre no topo.

## Instalação

Cola no terminal (instala global, funciona em qualquer projeto):

```bash
mkdir -p ~/.claude/skills && cd ~/.claude/skills && git clone https://github.com/yuri-pontes/ritual-skills.git _ritual-tmp && mv _ritual-tmp/ritual-* . && rm -rf _ritual-tmp
```

Pra instalar só num projeto, troca `~/.claude/skills` por `<seu-projeto>/.claude/skills`.

Depois é só rodar qualquer um dos rituais. Se você ainda não tem config, o Claude percebe e te configura na hora, uma pergunta por vez (leva 1 min).

## Setup: você escolhe o que acompanhar

O setup não joga uma planilha de 30 campos na sua cara. Ele pergunta quais áreas da sua vida você quer destravar agora e liga só as métricas dessas áreas:

| Área | Métricas |
|---|---|
| 🫀 Saúde física | treino, passos, peso, água, sol |
| 🧠 Saúde mental | humor, ansiedade, libido |
| 💰 Trabalho & dinheiro | trabalho profundo, tempo de tela, receita, gasto, avanço |
| 🤝 Relações & presença | saiu de casa, contato social real |
| 🚭 Vícios & escapes | cigarro, álcool, pornô (o "onde escapou") |
| 🎯 Projeto pessoal | você dá o nome (instrumento, escrita, esporte, estudo, o que for) |

Começa com uma ou duas áreas. Dá pra ligar mais quando quiser. Se você ligar tudo de uma vez, vai largar tudo junto em três dias e o ritual morre antes de pegar.

Tem um núcleo que fica sempre ligado, sem depender das áreas: sono, vitória do dia, onde você escapou, plano de amanhã e a nota do dia. É a espinha do sistema.

### Integrações (se você tiver)

Funciona 100% só com texto, sem conectar conta nenhuma. Se você usa, dá pra ligar no setup:

- **Google Calendar (via MCP):** já puxa sua agenda no check-in e na entrevista.
- **Gravador de call (Fathom, Otter e afins):** no fim do dia, compara o que ficou combinado nas calls com o que você registrou e te lembra do que faltou.

Mesmo sem integração nenhuma, o resgate do fim do dia continua rolando: o Claude te pergunta o que você fez e ainda não anotou.

## Por que os campos são padronizados

As métricas são salvas sempre no mesmo formato (`Sono: 7.5h`, `Água: 2L`, `Trabalho profundo: 4h`). É isso que deixa o `/ritual-analise` ler meses de histórico e te mostrar tendência depois. Diário escrito solto ninguém consegue analisar.

## Como pensar o uso

- O log é seu diário de bordo, guarda o que aconteceu. O backlog guarda as tarefas. Cada um no seu canto, sem misturar.
- Responde uma pergunta por vez, no seu ritmo. Cansou no meio da entrevista? Fala "fecha com o que tem" que o Claude encerra com o que já tem.
- O campo "onde escapou" é o que mais rende. É onde você é honesto sobre o que te derrubou no dia. Sem ele o log vira propaganda de você mesmo.
- Registra na hora. Se você esperar a noite, sua cabeça já reescreveu a história mais bonita do que foi.
- Começa pequeno. Uma ou duas coisas que você consegue manter rendem mais do que dez que você abandona.

## Funciona? (case real)

Antes de empacotar, rodei isso por um mês. Check-in em 30 dias diferentes, entrevista em 28, uma sequência de 13 dias sem furar, nota média 7,8. O que mais valeu foi parar de deixar cobrança, prazo e gasto caírem no meio do caminho, e ver no histórico padrões sobre mim que eu sentia mas não enxergava.

O relato completo, com os casos reais (anonimizados) e a parte honesta do que não funcionou de primeira, tá em [`CASE-STUDY.md`](CASE-STUDY.md).

## Mexer no que quiser

Tudo fica editável na config (`~/.ritual/config.json`): ligar e desligar áreas e métricas, renomear seu projeto pessoal, ativar integração. Se quiser mudar o jeito que as skills falam com você, é só editar o `SKILL.md` de cada uma, são curtos.

## Crédito

Sistema desenhado por Yuri Pontes, em cima de uma prática diária que virou hábito, e empacotado pra quem quiser se organizar e acompanhar a própria vida com método.

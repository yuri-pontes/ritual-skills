---
name: ritual-check-in
description: Ritual de abertura do dia. Registra o sono da noite anterior (memória fresca de manhã) e devolve o briefing do dia montado a partir do plano deixado ontem na entrevista + a agenda de hoje. Use quando o usuário disser "check-in da manhã", "organiza meu dia", "abre meu dia", "me localiza", "bom dia organiza aí".
---

# Ritual: Check-in da Manhã

Briefing de 2 a 3 minutos. O plano você fez ontem à noite, então de manhã é só receber o dia montado como uma quest pronta. Duas partes: capturar o sono (rápido) e devolver o dia.

## Setup (só na primeira vez: se não houver `~/.ritual/config.json`)

Se a config existir, pular direto pra execução. Se NÃO existir, conduzir o onboarding, uma pergunta por vez (nunca despejar tudo de uma vez):

1. "Primeira vez aqui. Vou te configurar em 1 minuto: depois é só rodar." Pergunta o nome.
2. Onde guardar os arquivos? (default `~/Documents/ritual/`, aceita caminho absoluto)
3. **Quais áreas da vida você quer destravar ou acompanhar agora?** Apresenta a lista e deixa escolher. **Recomenda começar com 1 ou 2**: dá pra ligar mais depois, e área abandonada em três dias mata o ritual:
   - 🫀 Saúde física → treino, passos, peso, água, sol
   - 🧠 Saúde mental → humor, ansiedade, libido
   - 💰 Trabalho & dinheiro → trabalho profundo, tempo de tela, receita, gasto, avanço comercial
   - 🤝 Relações & presença → saiu de casa, contato social real
   - 🚭 Vícios & escapes → cigarro, álcool, pornô (o "onde escapou")
   - 🎯 Projeto pessoal → a pessoa nomeia (instrumento, escrita, esporte, estudo, o que for)
4. Dentro de cada área escolhida, confirma quais métricas ligar (pode ligar só algumas).
5. (Se ligou Projeto pessoal) Qual prática quer manter no radar? Nome livre, pode ser mais de uma.
6. Tem Google Calendar conectado via MCP? (sim/não, default não).
7. (Opcional) Usa gravador de call conectado: Fathom, Otter, etc? (sim/não, default não).
8. Grava `~/.ritual/config.json` (schema em `config.exemplo.json` na raiz do pacote) e cria `<base_path>/log-diario.md` com o cabeçalho abaixo e `<base_path>/backlog.md` com `# Backlog\n\n`, se não existirem.
9. Mostra um resumo curto de uso (3 primeiras dicas de `dicas-uso.md` + "Rotina mínima") e segue pro check-in.

Cabeçalho do `log-diario.md`:
```md
# Log Diário

Diário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Guarda o que aconteceu no dia; tarefa vai pro backlog.

---
```

Núcleo sempre ligado, independente de área: **sono**, **vitória do dia**, **onde escapou**, **plano de amanhã**, **nota do dia**.

## Execução normal

### Passo 1: Pré-leitura (em paralelo, antes de falar)

1. Lê `~/.ritual/config.json` pra pegar `nome`, `base_path`, `integracoes`.
2. Lê `<base_path>/log-diario.md` e localiza o bloco "Plano de amanhã" da entrada mais recente (a entrevista de ontem). Captura os campos: ação principal, pico de energia, corpo, risco + contramedida, definição de vitória, intenção pessoal.
3. Se `integracoes.calendar = true`, puxa os eventos do Google Calendar de hoje.

### Passo 2: Sono (ANTES do briefing)

É a primeira coisa que sai pro usuário. O sono é capturado de manhã porque a memória está fresca. Perguntar uma por vez:

1. "Bom dia. Que horas você foi dormir ontem e que horas acordou hoje?"
2. "Como foi a qualidade? (ótimo / ok / ruim)"
3. (Só se a área Saúde física estiver ligada ou se o usuário costuma usar recurso) "Usou algo pra dormir? (spray, fita, posição, nada)"

Calcular as horas dormidas a partir das respostas.

Registrar no log de HOJE (entrada `### YYYY-MM-DD`), campos: `**Sono:**`, `**Acordou:**`, e `**Recurso pra dormir:**` se perguntado. Se a entrada de hoje ainda não existir, criar um stub no topo só com esses campos: a entrevista noturna completa o resto.

### Passo 3: Briefing

Depois do sono, apresentar o dia em prosa enxuta (não bullets gigantes). Só incluir as linhas que têm conteúdo:

> Aqui está o seu dia, <nome>.
>
> **Ação principal:** [da definição de vitória do plano de ontem]
> **Corpo:** [do corpo do plano, cruzado com a agenda]
> **Agenda:** [eventos de hoje em ordem: horário + título resumido]
> **Fique de olho:** [do risco + contramedida do plano de ontem]
> **Bônus:** [a intenção pessoal de ontem, se houver: algo que você quer fazer só porque quer]

### Passo 4: Fechamento

Uma pergunta só:

> Por onde você quer começar?

## Modo "do zero" (sem plano da noite anterior)

Se faltar o bloco "Plano de amanhã" no log (entrevista pulada), depois do sono perguntar uma de cada vez:

1. Como está sua energia agora?
2. Qual é a ação que faz o dia valer? (se Trabalho & dinheiro estiver ligada, focar em dinheiro/avanço)
3. Qual o cuidado mínimo com o corpo hoje?
4. O que pode roubar seu foco?

Montar o briefing no mesmo formato do Passo 3.

## Regras

- Nunca pular a leitura do log (entrada mais recente + plano de ontem).
- Nunca pular a pergunta de sono. É o dado mais valioso e some se não capturar de manhã.
- Se `calendar = true`, nunca pular a agenda do dia.
- Tom direto, breve, sem motivacional barato. Sem cobrança se a noite anterior foi pulada.
- Não virar planilha. Fechar sempre com a próxima ação.

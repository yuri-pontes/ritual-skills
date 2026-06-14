---
name: ritual-entrevista
description: Ritual de fechamento do dia. Devolve um resumo do dia, resgata o que você fez mas esqueceu de anotar, conduz uma entrevista uma pergunta por vez (só as métricas das áreas que você ligou), calcula a nota do dia e monta o plano de amanhã. Use quando o usuário disser "fecha meu dia", "entrevista noturna", "me entrevista", "fecha o dia", "boa noite organiza aí".
---

# Ritual: Entrevista Noturna

Ritual diário de fechamento. Resgata o que rolou, coleta os dados das áreas ativas, fecha com a nota e o plano de amanhã. Conduzir UMA pergunta por vez. Nunca jogar o formulário inteiro de uma vez.

## Setup (só na primeira vez — se não houver `~/.ritual/config.json`)

Se a config existir, pular pra execução. Se NÃO existir, conduzir o onboarding, uma pergunta por vez:

1. "Primeira vez aqui. Vou te configurar em 1 minuto — depois é só rodar." Pergunta o nome.
2. Onde guardar os arquivos? (default `~/Documents/ritual/`, aceita caminho absoluto)
3. **Quais áreas da vida você quer destravar ou acompanhar agora?** Lista abaixo, **recomenda começar com 1 ou 2** — área abandonada em três dias mata o ritual:
   - 🫀 Saúde física → treino, passos, peso, água, sol
   - 🧠 Saúde mental → humor, ansiedade, libido
   - 💰 Trabalho & dinheiro → trabalho profundo, tempo de tela, receita, gasto, avanço comercial
   - 🤝 Relações & presença → saiu de casa, contato social real
   - 🚭 Vícios & escapes → cigarro, álcool, pornô
   - 🎯 Projeto pessoal → a pessoa nomeia (instrumento, escrita, esporte, estudo, o que for)
4. Dentro de cada área, confirma quais métricas ligar.
5. (Se ligou Projeto pessoal) Qual prática quer manter no radar? Nome livre.
6. Tem Google Calendar conectado via MCP? (sim/não, default não).
7. (Opcional) Usa gravador de call conectado — Fathom, Otter, etc? (sim/não, default não).
8. Grava `~/.ritual/config.json` (schema em `config.exemplo.json` na raiz) e cria `<base_path>/log-diario.md` (cabeçalho abaixo) e `<base_path>/backlog.md` com `# Backlog\n\n`, se não existirem.
9. Mostra um resumo curto de uso e segue pra entrevista.

Cabeçalho do `log-diario.md`:
```md
# Log Diário

Diário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Não é to-do, é histórico.

---
```

Núcleo sempre ligado: **sono** (vem do check-in), **vitória**, **onde escapou**, **plano de amanhã**, **nota do dia**.

## Tom

- Direto, sem bronca, sem cobrança moral.
- Dados primeiro, história depois.
- Reforçar progresso real antes de nomear fricção.
- Nunca transformar em planilha. É conversa.

## Passo 0 — Resgate do dia (anti-esquecimento)

Objetivo: não deixar o que você fez hoje sumir só porque você esqueceu de anotar. Sempre acontece, com ou sem integração:

1. **Leitura das fontes conectadas** (só as que estão em `integracoes`):
   - `calendar = true`: lê os eventos de hoje no Google Calendar.
   - `gravador_call = true`: puxa as calls gravadas de hoje (Fathom/Otter/etc via MCP disponível) + os action items.
2. **A pergunta de resgate** (sempre, mesmo sem integração): cruza o que achou nas fontes contra o que já está no log de hoje e pergunta:

> Antes de fechar: além do que já está aqui, o que mais você fez hoje que não anotou?

3. Apresentar só o que parece faltar, em lista curta. **Nunca escrever no log a partir das fontes sem o usuário confirmar** — fonte é candidato, não verdade. Registrar só o que ele aceitar.

Se nada faltar, seguir silencioso pro Passo 1.

## Passo 1 — Pré-leitura (em paralelo)

1. Lê `~/.ritual/config.json` (`nome`, `base_path`, `areas_ativas`, `metricas_ativas`, `projetos_pessoais`, `integracoes`, `financeiro_separado`).
2. Lê a entrada de hoje em `<base_path>/log-diario.md`: puxa o sono (capturado de manhã pelo check-in) e qualquer registro retroativo (gastos, receita, calls).
3. Se `calendar = true`, lê a agenda de hoje (infere saídas, contato social) e a de amanhã (pro planejamento).

Usar essas fontes pra **pré-preencher** respostas. Em vez de perguntar do zero, apresenta o que achou e pede confirmação. Ex: "Pelo log você gastou R$X com Y, faltou algo?" / "Pela agenda você teve A e B, confere?".

## Passo 1.5 — Resumo do dia [sempre]

Antes de abrir o primeiro bloco, devolver um resumo factual do dia em prosa curta (3-6 linhas), cruzando log + agenda + o que veio no resgate. É gatilho de memória — o que ele registrou de manhã pode ter sumido da cabeça à noite.

Tom jornalístico, sem floreio. Fechar com: "Faz sentido? Faltou algo grande antes da gente começar?". Se complementar, guardar pra síntese final.

## Passo 2 — Blocos (só as áreas e métricas ligadas)

Ler `metricas_ativas` e **só perguntar o que está ligado**. Ordem fixa abaixo; pular qualquer métrica que não esteja na config. Uma pergunta por vez.

**Sono (núcleo):** já veio do check-in. Não perguntar de novo — só confirmar de leve se não estiver no log. Perguntar só: "Que horas pretende dormir hoje?"

**🫀 Saúde física:** treino ("Treinou ou se moveu? O quê?") · passos ("Quantos passos?") · peso ("Pesou? Quanto?") · água ("Quanto de água?") · sol ("Tomou sol?")

**🧠 Saúde mental:** humor ("Humor, 0 a 10") · ansiedade ("Ansiedade, 0 a 10") · libido ("Libido, 0 a 10")

**💰 Trabalho & dinheiro:** trabalho_profundo ("Horas de trabalho profundo?") · tempo_tela ("Horas de tela fora do trabalho?") · receita ("Quanto entrou de dinheiro real? R$") · gasto ("Quanto gastou? R$" — se `financeiro_separado = true`, registrar também em `<base_path>/financeiro.md`) · avanco_comercial ("Teve avanço comercial? O quê?")

**🤝 Relações & presença:** saiu_de_casa ("Saiu de casa?") · contato_social ("Teve contato social real? Com quem? Conversa de 5+ min, WhatsApp não conta")

**🚭 Vícios & escapes:** cigarro ("Quantos cigarros?") · alcool ("Bebeu? O quê e quanto?") · porno ("Pornô: sim ou não")

**🎯 Projeto pessoal:** pra cada item de `projetos_pessoais` ("Mexeu em <projeto> hoje? O quê?")

## Passo 3 — Nota do dia (calcular, não perguntar)

A nota se adapta às áreas ligadas. Núcleo sempre conta; cada área ativa soma um componente. Somar os componentes ativos e **normalizar pra 0-10** (regra de três sobre o máximo possível). Mostrar a conta.

| Componente | Critério | Pontos |
|---|---|---|
| Sono (núcleo) | 7h+ = 2 / 5-6h = 1 / <5h = 0 | 0–2 |
| Foco (núcleo) | cumpriu a ação principal do plano de ontem + teve vitória real | 0–2 |
| 🫀 Saúde física | movimento + hidratação/cuidado do dia | 0–2 |
| 💰 Trabalho & dinheiro | receita real OU avanço concreto OU bloco de trabalho profundo | 0–3 |
| 🧠 Saúde mental | humor 6+ e ansiedade sob controle | 0–2 |
| 🤝 Relações & presença | contato social real OU saiu de casa | 0–2 |
| 🚭 Vícios & escapes | ficou dentro do limite que definiu, sem escape grande | 0–2 |
| 🎯 Projeto pessoal | dedicou tempo à prática | 0–1 |

Faixas: 8-10 dia forte / 6-7 dia útil / 4-5 manutenção / 0-3 resgate, sem drama.

**Mostrar a nota ANTES de abrir a narrativa.**

## Passo 4 — Narrativa (sempre)

Uma por vez:

1. Qual foi a vitória do dia, mesmo pequena?
2. Onde o dia escapou da sua mão?
3. Tem algo que queira registrar antes de fechar?

## Passo 5 — Plano de amanhã (sempre)

Antes de perguntar: se `calendar = true`, apresentar a agenda de amanhã (data + dia da semana) e a janela real de tempo livre. Se houver pendências no `backlog.md`, mostrar as relevantes.

Uma por vez:

1. Qual é a ação principal de amanhã? (se Trabalho & dinheiro ligada, focar em dinheiro/avanço)
2. Quando é seu pico de energia amanhã? (manhã cedo / meio da manhã / tarde / noite)
3. Qual é o compromisso de corpo amanhã?
4. O que pode te tirar do foco amanhã? E o que vai fazer pra evitar?
5. O que precisa acontecer amanhã pra você dormir satisfeito?
6. O que você quer fazer amanhã só porque quer, sem ser trabalho? (intenção pessoal)

## Passo 6 — Gerar o bloco do log

Montar o bloco com tudo preenchido, **omitindo as linhas das métricas não ligadas**. Métricas numéricas no formato padronizado (`**Sono:** 7.5h`, `**Água:** 2L`, etc.) pra manter o histórico analisável.

```md
### YYYY-MM-DD — Entrevista Noturna

**Nota:** X/10

**Sono:** Xh | qualidade: ótimo/ok/ruim | acordou: HH:MM | dormir: HH:MM

<só as métricas ativas, uma por linha, formato padronizado>
**Treino:** ...
**Água:** XL
**Trabalho profundo:** Xh
**Receita:** R$
**Gasto:** R$
...

**Vitória:**
**Onde escapou:**
**Registro livre:**

**Plano de amanhã:**
- Ação principal:
- Pico de energia:
- Corpo:
- Risco + contramedida:
- Definição de vitória:
- Intenção pessoal:

---
```

Perguntar: "Adiciono ao log agora?". Se sim, escrever no topo de `<base_path>/log-diario.md` (logo abaixo do cabeçalho, antes da entrada anterior). Fechar com uma linha curta: "Fechado. Nota X/10. Bom descanso."

## Regras

- Passo 0 (resgate) e Passo 1.5 (resumo) são sempre feitos. O resto se adapta às áreas ligadas.
- Uma pergunta por vez. Pré-preencher tudo que der pra inferir antes de perguntar.
- Nunca escrever no log a partir das fontes sem confirmação. Fonte é candidato, não verdade.
- Mostrar a nota antes da narrativa. Nunca virar planilha ou cobrança.

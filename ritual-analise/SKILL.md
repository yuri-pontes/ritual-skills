---
name: ritual-analise
description: Lê o histórico do log-diário e devolve o painel pessoal — disciplina (streaks de consistência), progresso das métricas e a análise do que tem dado certo ou errado (tendências e correlações). É aqui que o tracking vira decisão. Use quando o usuário disser "como eu tô indo", "analisa meu histórico", "meu progresso", "dashboard", "o que tá dando certo", "tendências", "ritual de análise".
---

# Ritual: Análise

O painel do sistema. Os outros rituais alimentam o histórico; este lê o histórico e devolve sentido. Três entregas: **disciplina** (você está aparecendo?), **progresso** (pra onde as métricas vão?) e **o que deu certo ou errado** (padrões e correlações). É o que separa este sistema de um diário comum.

## Setup (só na primeira vez — se não houver `~/.ritual/config.json`)

Se a config existir, pular pra execução. Se NÃO existir, conduzir o onboarding, uma pergunta por vez (mesma lista das outras skills):

1. Nome. 2. Onde guardar (default `~/Documents/ritual/`). 3. **Áreas da vida** a acompanhar (🫀 Saúde física / 🧠 Saúde mental / 💰 Trabalho & dinheiro / 🤝 Relações & presença / 🚭 Vícios & escapes / 🎯 Projeto pessoal), **começando com 1 ou 2**. 4. Métricas de cada área. 5. (Se Projeto pessoal) nome livre da prática. 6. Google Calendar via MCP? 7. Gravador de call? 8. Grava `~/.ritual/config.json` + cria `<base_path>/log-diario.md` e `<base_path>/backlog.md` se não existirem. 9. Resumo curto de uso.

> Nota: numa instalação nova quase não há histórico pra analisar. Se o log tiver menos de ~5 entradas, dizer isso com franqueza ("ainda tem pouco histórico — volte aqui depois de uns 7-10 dias de ritual") e oferecer o pouco que dá.

## Execução

### 1. Pré-leitura

1. Lê `~/.ritual/config.json` (`base_path`, `log_file`, `metricas_ativas`).
2. Lê `<base_path>/<log_file>` inteiro.
3. Pergunta o período (se não veio no pedido): **últimos 7 dias / 30 dias / tudo**. Default 30.

### 2. Parsing

Percorre as entradas do período e extrai os campos padronizados (`**Label:** valor`). Por isso o formato fixo importa — `**Sono:** 7.5h` é parseável, "dormi razoável" não é. Quando um campo estiver em prosa solta, fazer o melhor esforço e sinalizar baixa confiança naquele ponto.

Coletar: nota do dia, sono, e cada métrica em `metricas_ativas` ao longo do tempo. Também os campos qualitativos (vitória, onde escapou) pra leitura de padrões.

### 3. Painel — três seções

**A) Disciplina (consistência)**
- Streak atual e maior streak do ritual (dias seguidos com entrada no log).
- Por métrica-chave, a taxa de aderência no período ("treinou em 9 dos últimos 14 dias").
- Onde a corrente quebrou e em que dia da semana ela costuma quebrar.

**B) Progresso (pra onde vai)**
- Pra cada métrica numérica ativa: média do período, mínimo/máximo, e a direção vs. o período anterior (subindo / estável / caindo). Ex: "Sono: média 6.8h (era 6.2h no mês passado, subindo). Trabalho profundo: média 3.1h (caindo)."
- Distribuição das notas: quantos dias fortes / úteis / manutenção / resgate.

**C) O que deu certo ou errado (padrões)**
- Correlações legíveis entre métricas e a nota/estado. Ex: "Suas notas 8+ quase sempre têm 7h+ de sono e contato social real. Os dias de resgate concentram tela alta + zero movimento."
- Padrões no "onde escapou": o escape se repete? Tem gatilho (dia da semana, depois de tal coisa)?
- 1 a 3 observações acionáveis, conservadoras. Não inventar causa onde só há coincidência — se a amostra é pequena, dizer "indício, não conclusão".

### 4. Fechamento

Uma pergunta que vira ação:

> Quer que eu transforme alguma dessas observações em meta pro próximo período? (vira linha no backlog)

## Regras

- Só afirmar o que os dados sustentam. Amostra pequena = indício, não conclusão. Nunca inflar correlação em causa.
- Não dar bronca. O painel mostra o real, sem moralizar o resgate.
- Quando um campo não é parseável, dizer — não chutar número.
- Números sempre com o período de referência ("média 6.8h nos últimos 30 dias"), nunca soltos.
- Se faltar histórico, ser honesto sobre o limite em vez de forçar análise.

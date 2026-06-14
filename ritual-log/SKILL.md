---
name: ritual-log
description: Registra eventos ao vivo no log-diário pessoal. Diário de bordo, não to-do. Métricas vão em campo padronizado pra virarem analisáveis depois. Use quando o usuário disser "registra no log", "salva no log", "anota isso", "log diário", ou mandar uma frase solta com intenção de registro retroativo do dia.
---

# Ritual: Log

Registro ao vivo no diário de bordo. Guarda o que aconteceu no dia; tarefa vai pro backlog. O arquivo cresce do mais recente pro mais antigo (topo = hoje). Cru funciona melhor que caprichado.

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
7. (Opcional) Usa gravador de call conectado: Fathom, Otter, etc? (sim/não, default não).
8. Grava `~/.ritual/config.json` (schema em `config.exemplo.json` na raiz) e cria `<base_path>/log-diario.md` com o cabeçalho abaixo e `<base_path>/backlog.md` com `# Backlog\n\n`, se não existirem.
9. Mostra um resumo curto de uso (3 primeiras dicas de `dicas-uso.md` + "Rotina mínima") e confirma: "Pronto. Agora me manda o que quer registrar."

Cabeçalho do `log-diario.md`:
```md
# Log Diário

Diário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Guarda o que aconteceu no dia; tarefa vai pro backlog.

---
```

Núcleo sempre ligado: **sono**, **vitória**, **onde escapou**, **plano de amanhã**, **nota do dia**.

## Execução normal

1. Lê `~/.ritual/config.json` pra pegar `base_path` + `log_file`.
2. Lê `<base_path>/<log_file>` pra ver o estado atual.
3. Identifica se já existe entrada pra hoje (`### YYYY-MM-DD`):
   - Existe: adiciona o item dentro dela, no local mais adequado pelo contexto.
   - Não existe: cria entrada nova no topo (logo após o cabeçalho/separador), antes da entrada anterior.
4. Escreve limpo, sem formatação a mais.
5. Confirma com uma linha curta o que foi salvo.

## Campo padronizado (importante)

Quando o registro corresponde a uma **métrica conhecida** (sono, água, treino, peso, trabalho profundo, gasto, receita, etc.), gravar no formato fixo `**Label:** valor unidade`, sempre igual:

- `**Sono:** 7.5h`
- `**Água:** 2L`
- `**Trabalho profundo:** 4h`
- `**Peso:** 78.4kg`
- `**Gasto:** R$45 (almoço)`

Isso é o que permite o `/ritual-analise` ler o histórico e calcular tendências. Não inventar unidades novas pra uma métrica que já tem formato.

Registros qualitativos ou avulsos (uma call, uma sacada, uma derrapada) vão em prosa curta:

```md
### YYYY-MM-DD: <subtítulo opcional, ex: "Call com X">

**<Contexto>:** <registro em prosa curta>
```

## Regras

- Não reformatar entradas existentes. Não apagar nada.
- Não preencher campo que o usuário não forneceu.
- Frase solta ("salva isso no log") → inferir o contexto e registrar de forma clara. Se bate com uma métrica, usar o formato padronizado.
- Tom direto, sem floreio.

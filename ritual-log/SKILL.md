---
name: ritual-log
description: Registra eventos ao vivo no log-diário pessoal do usuário. Diário de bordo, não to-do. Use quando o usuário disser "registra no log", "salva no log", "adiciona no log", "log diário", "anota isso", ou mandar uma frase solta com intenção de registro retroativo do dia.
---

# Ritual: Log

Registro ao vivo no diário de bordo. Não é to-do, é histórico. O arquivo cresce do mais recente pro mais antigo (topo = hoje).

## Setup obrigatório (rodar só se não houver config)

Antes de qualquer coisa, verifica se existe `~/.ritual/config.json`. Se NÃO existir, executa o onboarding:

1. Cumprimenta curto: "É a primeira vez que você usa o Ritual. Vou te configurar em 1 minuto."
2. Pergunta uma de cada vez:
   - Teu nome (pra personalizar saudações)
   - Onde guardar os arquivos do ritual (default: `~/Documents/ritual/`, aceita absoluto)
   - Tem Google Calendar conectado via MCP nesse Claude? (sim/não, default não)
   - Quer ligar quais blocos opcionais da entrevista noturna agora? (lista abaixo, multi-select, default só os marcados)
     - [x] sono, [x] dinheiro, [x] vitória, [x] onde escapou, [x] plano de amanhã (sempre ligados, base)
     - [x] água, [x] remédios, [ ] passos, [ ] peso, [ ] sol, [ ] banho
     - [x] humor 0-10, [ ] ansiedade 0-10, [ ] libido 0-10
     - [ ] álcool, [ ] cigarros, [ ] pornô
     - [x] trabalho profundo (horas), [ ] tempo de tela, [ ] conteúdo postado
     - [ ] saiu de casa, [x] contato social, [ ] música/projeto pessoal
3. Cria `~/.ritual/config.json`:
```json
{
  "nome": "<nome>",
  "base_path": "<path>",
  "log_file": "log-diario.md",
  "backlog_file": "backlog.md",
  "calendar_mcp": <bool>,
  "blocos_ativos": [<lista dos marcados>],
  "criado_em": "<YYYY-MM-DD>"
}
```
4. Cria `<base_path>/log-diario.md` com o cabeçalho:
```md
# Log Diário

Diário de bordo. Cresce do mais recente pro mais antigo (topo = hoje). Não é to-do, é histórico.

---
```
5. Cria `<base_path>/backlog.md` vazio com `# Backlog\n\n` se não existir.
6. Lê `dicas-uso.md` (mesma pasta dessa skill) e exibe pro usuário um resumo curto: as 3 primeiras dicas da seção "O que faz a diferença" + o trecho "Rotina mínima diária". Não despeja o arquivo inteiro, só o essencial pra entender como o sistema é usado no dia a dia. Avisa que o arquivo completo está em `<pasta-da-skill>/dicas-uso.md` pra leitura quando quiser.
7. Confirma: "Pronto. Agora me manda o que quer registrar."

## Execução normal

1. Lê `~/.ritual/config.json` pra pegar `base_path` + `log_file`.
2. Lê `<base_path>/<log_file>` pra ver o estado atual.
3. Identifica se já existe entrada pra hoje (formato `### YYYY-MM-DD`):
   - Se existir: adiciona o novo item dentro dela, no local mais adequado pelo contexto.
   - Se não existir: cria nova entrada no topo do arquivo (logo depois do cabeçalho/separador), antes da entrada mais recente.
4. Escreve limpo, sem formatação a mais.
5. Confirma com uma linha curta o que foi salvo.

## Formato de nova entrada

```md
### YYYY-MM-DD — <subtítulo opcional, ex: "Manhã" ou "Call com X">

**<Contexto>:** <registro em prosa curta, sem bullet desnecessário>
```

Subtítulo é opcional. Se for anotação avulsa, usa só a data.

## Regras

- Não reformatar entradas existentes
- Não apagar nada
- Não preencher campos que o usuário não forneceu
- Frase solta ("salva isso no log") → inferir o contexto e registrar de forma clara
- Manter tom direto, sem floreio

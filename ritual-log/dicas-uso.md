# Dicas de uso (do autor)

O Ritual foi desenhado em torno de 4 hábitos. Vale entender como o sistema rende mais.

## Rotina mínima diária

- **Manhã (~3 min):** `/ritual-check-in`. Recebe o dia já organizado.
- **Durante o dia (~10s cada):** `/ritual-log <frase solta>`. Registra ao vivo. Quanto mais cru, melhor.
- **Noite (~5-10 min):** `/ritual-entrevista`. Fecha o dia. Sai a nota e o plano de amanhã (que vira gancho do check-in).

`/ritual-backlog` roda **semanal** (ou quando o log inflar). Não é diário.

## O que faz a diferença

1. **Registra ao vivo, não de memória.** Frase crua tipo "salva no log: fechei call com Joãozinho, toparam piso de 8k" funciona melhor do que esperar a noite. À noite o cérebro reescreve a história bonito demais.

2. **O campo "onde escapou" é o mais importante.** Onde você derrapou (celular, evitou call difícil, comeu besteira). Sem ele, o log vira marketing pessoal.

3. **A entrevista é conversa, não formulário.** Se cansou no meio, fala "fecha aí com o que tem". O Claude sintetiza com o que coletou. Não trava.

4. **Plano de amanhã não é opcional.** É o gancho do check-in da manhã. Sem ele, a manhã vira pergunta do zero, mais fricção.

5. **Pré-preenchimento.** Se você ligou Google Calendar no setup, a entrevista já puxa eventos do dia. Você só confirma. Economiza 2 minutos.

6. **Log ≠ to-do.** Nunca trate o log como lista de tarefas. Ele é histórico. Pendências moram no `backlog.md`, populadas pelo `/ritual-backlog`.

7. **Customização.** Os blocos da entrevista (cigarro, álcool, libido, peso, passos, etc) são modulares. Edita `~/.ritual/config.json` pra ligar/desligar campos sem refazer o setup.

8. **Comece pequeno.** Liga só os blocos que você de fato quer trackear. Adicionar campo depois é fácil. Trackear campo que você abandona em 3 dias mata o ritual.

## Sinais de que tá funcionando

- Você termina o dia com a cabeça mais leve (despejou no log, não fica circulando na cabeça).
- A manhã vira execução, não decisão.
- Padrões aparecem na semana (energia baixa em dia X, escape sempre depois de Y).
- Backlog tem entradas que vieram das suas próprias palavras, não de ansiedade aleatória.

## Sinais de que tá indo pro buraco

- Pulou 3 entrevistas seguidas. **Solução:** roda mesmo curta. 2 minutos vale mais que zero.
- O log virou propaganda (só vitória, zero "escapou"). **Solução:** força um "onde escapou" mesmo que pequeno.
- Backlog inflou e ninguém olha. **Solução:** roda `/ritual-backlog` no escopo "tudo" e faz uma faxina.

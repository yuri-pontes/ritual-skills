# Dicas de uso (do autor)

O Ritual é um **dashboard pessoal**: você acompanha o que importa na sua vida, cria disciplina aparecendo todo dia, e depois analisa o que tem dado certo ou errado. Cinco rituais sustentam isso — três diários, um semanal, um sob demanda.

## Rotina mínima diária

- **Manhã (~3 min):** `/ritual-check-in`. Registra o sono (memória fresca) e recebe o dia já montado.
- **Durante o dia (~10s):** `/ritual-log <frase solta>`. Registra ao vivo. Quanto mais cru, melhor.
- **Noite (~5-10 min):** `/ritual-entrevista`. Fecha o dia. Sai a nota e o plano de amanhã (que vira o gancho do check-in).

`/ritual-backlog` roda **semanal** (puxa pendências do log). `/ritual-analise` roda **quando você quiser ver o progresso** — funciona melhor depois de 1-2 semanas de histórico.

## O que faz a diferença

1. **Registra ao vivo, não de memória.** "Salva no log: fechei a call, toparam o orçamento" vale mais que esperar a noite. À noite o cérebro reescreve a história bonita demais.
2. **O campo "onde escapou" é o mais importante.** Onde você derrapou (celular, evitou a call difícil, comeu besteira). Sem ele, o log vira marketing pessoal.
3. **A entrevista é conversa, não formulário.** Cansou no meio? "fecha aí com o que tem". O Claude sintetiza com o que tem. Não trava.
4. **Plano de amanhã não é opcional.** É o gancho do check-in. Sem ele, a manhã vira pergunta do zero, mais fricção.
5. **Comece com 1-2 áreas.** Área que você abandona em três dias mata o ritual inteiro. Adicionar depois é fácil — editar a área que você não usa custa caro.
6. **Log ≠ to-do.** O log é histórico. Pendências moram no backlog, populadas pelo `/ritual-backlog`.
7. **Consistência > intensidade.** Aparecer todo dia, mesmo curto, é o que cria disciplina — e o que gera dado pra análise valer alguma coisa.
8. **Depois de ~2 semanas, roda `/ritual-analise`.** É quando o sistema começa a te mostrar padrão que você não enxergava sozinho. Sem histórico, não há análise.

## Sinais de que tá funcionando

- Você termina o dia com a cabeça mais leve (despejou no log, não fica circulando).
- A manhã vira execução, não decisão.
- Padrões aparecem (energia baixa em dia X, escape sempre depois de Y).
- O backlog tem entradas que vieram das suas palavras, não de ansiedade aleatória.

## Sinais de que tá indo pro buraco

- Pulou 3 entrevistas seguidas. **Solução:** roda mesmo curta. 2 minutos vale mais que zero.
- O log virou propaganda (só vitória, zero "escapou"). **Solução:** força um "onde escapou", mesmo pequeno.
- Ligou áreas demais e parou de preencher. **Solução:** corta pra 1-2 na config e volta a aparecer.
- Backlog inflou e ninguém olha. **Solução:** roda `/ritual-backlog` no escopo "tudo" e faz uma faxina.

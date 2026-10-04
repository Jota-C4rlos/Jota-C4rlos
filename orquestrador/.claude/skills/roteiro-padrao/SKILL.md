---
name: roteiro-padrao
description: Método padrão de roteiro do pilar roteiro para vídeos curtos feitos com IA (15 s a 3 min) - premissa, estrutura por duração, formato de cena, personagens pelo comportamento, universo e escrita pensando em continuidade. Use quando a ordem trouxer MÉTODO roteiro-padrao ou não trouxer MÉTODO.
user-invocable: false
---
# Roteiro padrão

Método profissional de roteiro para vídeo curto feito com IA, de 15 s a 3 min. É o padrão até o método da Pilli Academy ficar pronto, e depois continua como alternativa. Junta o ofício clássico de roteiro (premissa, estrutura, cena, subtexto, plantar e pagar) com o que a geração por IA exige: ação física clara e continuidade escrita.

Os modelos dos três entregáveis e um exemplo curto estão em .claude/skills/roteiro-padrao/modelos.md: leia antes de escrever.

## Passo a passo
1. Leia o conceito aprovado e o briefing. Anote a duração-alvo, o formato, o idioma das falas e os inegociáveis.
2. Escreva a premissa e a ideia controladora (seção 1).
3. Monte a bíblia de personagens pelo comportamento: personagens_vNN.md.
4. Monte o universo (regras, época, tom, locações com função e geografia): universo_vNN.md.
5. Escolha a estrutura pela duração (seção 2) e faça a escaleta: uma linha por cena, com o tempo. A soma bate com a duração-alvo antes de escrever qualquer cena.
6. Escreva as cenas no formato da seção 3, com as regras das seções 4 e 5.
7. Marque as cenas de alto risco de geração, cada uma com uma saída (seção 6).
8. Passe o checklist (seção 7) e salve roteiro_vNN.md.

## 1. Premissa e ideia controladora
- **Premissa**: a história numa frase: personagem + o que quer + o que impede + o que muda. Ex.: "Um filho que não fala com o pai há anos vai devolver uma ferramenta e descobre que o pai nunca deixou de esperar por ele."
- **Ideia controladora**: o que a história diz, numa frase (um valor e a sua causa). Ex.: "O perdão chega quando alguém mostra que nunca deixou de esperar." Toda cena serve a ela; a que não serve sai.
- **Pergunta dramática**: o que o gancho pergunta e o clímax responde ("Ele vai entrar?"). Em vídeo curto, ela aparece nos 3 primeiros segundos.
- Anúncio ou conteúdo de marca: a ideia controladora é a mensagem única do briefing, contada por uma história, não dita.

## 2. Estrutura por duração
Blocos: **gancho** (a pergunta visual), **mundo e contexto** (quem, onde, o que quer), **incidente** (o que tira tudo do lugar), **escalada** (a pressão sobe em passos), **virada** (a surpresa ou o ponto sem volta), **clímax e payoff** (a resposta; o que foi plantado é pago), **fechamento ou CTA** (a última imagem; CTA só se o briefing pedir).

Quanto menor o vídeo, mais blocos se fundem. Os tempos são referência: ajuste ao conceito, mas o gancho fica sempre em 0–3 s e o fechamento no fim. Para durações intermediárias (45 s, 90 s), mantenha as proporções da tabela mais próxima.

**~15 s · 1 a 3 cenas**
| Bloco | Tempo | O que fazer |
|---|---|---|
| Gancho + mundo | 0–3 s | a imagem que levanta a pergunta já mostra onde estamos |
| Incidente + escalada | 3–10 s | uma coisa muda e aperta, num passo só |
| Virada, clímax e payoff | 10–13 s | a resposta inesperada |
| Fechamento ou CTA | 13–15 s | a imagem que fica |

**~30 s · 3 a 5 cenas**
| Bloco | Tempo | O que fazer |
|---|---|---|
| Gancho | 0–3 s | pergunta visual, sem explicar |
| Mundo e contexto | 3–7 s | quem é, onde está, o que quer |
| Incidente | 7–11 s | o problema chega |
| Escalada | 11–20 s | 2 passos, cada um pior que o anterior |
| Virada | 20–24 s | a surpresa muda o sentido do que vimos |
| Clímax e payoff | 24–28 s | a resposta; o plantado é pago |
| Fechamento ou CTA | 28–30 s | última imagem ou chamada |

**~60 s · 5 a 8 cenas**
| Bloco | Tempo | O que fazer |
|---|---|---|
| Gancho | 0–3 s | pergunta visual |
| Mundo e contexto | 3–10 s | plante aqui o que vai ser pago no fim |
| Incidente | 10–15 s | o problema chega |
| Escalada | 15–38 s | 3 passos; um respiro curto antes da virada |
| Virada | 38–45 s | ponto sem volta |
| Clímax e payoff | 45–55 s | a resposta |
| Fechamento ou CTA | 55–60 s | última imagem ou chamada |

**~180 s · 10 a 18 cenas**
| Bloco | Tempo | O que fazer |
|---|---|---|
| Gancho | 0–3 s (cold open até 10 s) | o momento mais forte, ou uma amostra dele |
| Mundo e contexto | até 30 s | quem, onde, o que quer; plantar |
| Incidente | 30–40 s | o problema chega |
| Escalada 1 | 40–90 s | a pressão sobe |
| Ponto médio | ~90 s | uma revelação muda o jogo |
| Escalada 2 | 90–130 s | agora com mais a perder |
| Virada | 130–145 s | o pior momento ou o ponto sem volta |
| Clímax e payoff | 145–170 s | a resposta |
| Fechamento ou CTA | 170–180 s | última imagem ou chamada |

Em 3 min, renove a pergunta a cada 20 a 30 s (um mistério novo, uma ameaça, uma revelação). É prática de retenção em vídeo curto, não regra fixa: confira com os DNAs do projeto.

## 3. Formato de cena
Adaptado do formato de roteiro de cinema para markdown:

```markdown
### CENA 3 — INT. OFICINA DOS FUNDOS — DIA — 10 s
Bloco: escalada · Em cena: Rui, Antônio
Ação: frases curtas, no presente, só o que a câmera vê e o microfone ouve. Um parágrafo por momento.
RUI (irônico — se defende da emoção): "Ainda tem tudo isso?"
Som: ambiente, efeitos, o silêncio que importa.
NOTA DE DIREÇÃO (sugestão): o que o roteirista imagina de plano, ritmo ou atuação. Quem decide é o José.
CONTINUIDADE: quem entra e sai (ordem e lado) · portas · objetos e mãos · luz e hora · estado físico
RISCO DE GERAÇÃO: baixo, médio ou alto — o quê — saída
```

- **Cabeçalho**: CENA N — INT. (interna) ou EXT. (externa) — LOCAL (o mesmo nome do universo) — DIA, NOITE, AMANHECER ou ENTARDECER — duração em segundos. Cena sem corte de tempo em relação à anterior: acrescente "CONTINUA".
- **Personagem** em MAIÚSCULAS na primeira aparição na ação. Idade só se a trama precisar.
- **Fala**: PERSONAGEM (intenção): "fala". A intenção é o que ele quer com a fala, não só o tom: "(desconfiado — quer saber se está sozinho)".
- **Off**: NARRADOR (off) ou PERSONAGEM (off) para voz fora de quadro.
- **Texto na tela** só se o briefing pedir: TEXTO NA TELA: "...". Por padrão, vai para a pós.
- **Cortes naturais**: dentro de uma cena longa, marque "Corte:" onde o plano muda naturalmente. O pilar prompts divide o roteiro em takes pelo limite do modelo de vídeo, e cortes naturais facilitam essa divisão.
- **Notas de direção** são sugestões ao diretor. Nada de lente, prompt ou aparência.
- As linhas CONTINUIDADE e RISCO DE GERAÇÃO entram quando houver o que dizer.

## 4. Regras de ofício
- **Mostre, não diga.** Emoção vira ação visível: gesto, olhar, pausa, objeto. "Ela está triste" não é filmável; "ela vira o porta-retrato para baixo" é. Na IA isso vale em dobro: a atuação gerada só mostra o que está descrito.
- **Uma ideia por cena.** Cada cena tem um propósito e vira alguma coisa: começa num estado e termina noutro (confiança → desconfiança). Cena que não vira nada sai.
- **Cada cena paga o tempo que ocupa.** Comece a cena no meio da ação e corte assim que ela virar.
- **Subtexto.** O personagem raramente diz o que sente. A fala diz uma coisa; a ação mostra outra.
- **Plantar e pagar.** Todo objeto, fala ou detalhe que ganha destaque é pago depois; todo payoff foi plantado antes. Em vídeo curto, plante cedo (no mundo) e pague no clímax.
- **Fala curta.** Uma ou duas frases por vez. Para caber no take, conte cerca de 2 a 3 palavras por segundo de fala, mais as pausas (referência prática de ritmo de conversa; o José ajusta na geração).
- **Gancho visual antes do verbal.** Abra com uma imagem que levanta a pergunta, não com uma fala que explica.
- **Funciona sem som.** Para redes, a história se entende sem som. Fala e música somam; não carregam a história sozinhas.
- **Específico.** Detalhe concreto vale mais que adjetivo: "o relógio parado às 6h15", não "um relógio antigo".
- **O personagem age pelo que quer.** Toda ação nasce do objetivo da bíblia; a reação sob pressão mostra quem ele é.

## 5. Escrever pensando em continuidade
O vídeo é gerado em takes separados, e o modelo não lembra o take anterior. O roteiro já resolve a lógica física, para os pilares visual e prompts só traduzirem.
- **Entradas e saídas**: diga quem entra primeiro, por onde e por qual lado. Quem sai primeiro chega primeiro na cena seguinte: se Rui sai na frente, no corte seguinte ele está na frente e Antônio atrás.
- **Portas**: diga de que lado fica a dobradiça e para onde a porta abre (para dentro ou para fora do cômodo). A mesma porta abre sempre para o mesmo lado: quem entra empurrando sai puxando, e quem entra puxando sai empurrando. Porta vai-e-vem é exceção e fica escrita no universo.
- **Objetos**: em que mão estão, onde são largados e onde estão na cena seguinte. Nada some nem aparece sem uma ação.
- **Posição e olhar**: num diálogo, quem fica de cada lado. Mantenha até uma ação mudar.
- **Luz e hora**: a hora não pula sem corte de tempo. Mudou, marque no cabeçalho (MAIS TARDE, NOITE).
- **Estado físico e figurino**: molhado, sujo, ferido, sem casaco, continua até uma ação mudar. Troca de roupa só com motivo, escrita na ação.
- **Geografia**: use os nomes e a geografia das locações do universo. Repita em cada cena o que importa para a ação; não confie no "já foi dito".

## 6. Cenas de alto risco de geração
São de alto risco: portas e objetos mecânicos, entradas e saídas, 3 ou mais personagens em cena, mãos manipulando objetos (montar, dobrar, amarrar), líquidos, texto na tela (placas, bilhetes, etiquetas), diálogo longo, ação rápida (luta, queda, corrida), multidão e o personagem que gira de costas para a frente. Marque cada uma e dê uma saída de roteiro que não mude a história.

| Risco | Saídas de roteiro |
|---|---|
| Porta | começar com a porta já aberta; cortar no meio da ação; a entrada acontece fora do quadro |
| 3 ou mais personagens | dividir em cenas de 1 ou 2; os outros em off ou de costas |
| Mãos e objetos | mostrar o antes e o depois; cortar a manipulação |
| Texto na tela | resolver na pós; trocar por imagem (foto, desenho, símbolo) |
| Diálogo longo | dividir entre cenas; trocar fala por ação |
| Ação rápida | dividir em preparação e resultado; um gesto só por vez |
| Líquidos | mostrar o resultado, não o processo (copo já cheio, chão já molhado) |

As falhas relatadas no Seedance 2.5 (porta que gira sem dobradiça, figurino que muda ao longo da sequência, identidade que se perde com 3 ou mais personagens, deformação em ação rápida, texto na tela fraco) vêm de testes de terceiros: a confirmar nos takes do José. A mesma lista de risco está em _Sistema/checklist-viabilidade.md (item 7).

## 7. Checklist final
- [ ] Premissa e ideia controladora no topo; conceito aprovado e inegociáveis preservados.
- [ ] Escaleta com acumulado; a soma dos tempos é a duração-alvo.
- [ ] O gancho (0–3 s) levanta uma pergunta e o fechamento responde.
- [ ] Toda cena vira alguma coisa e paga o tempo que ocupa.
- [ ] Tudo o que foi plantado é pago; nada é pago sem ter sido plantado.
- [ ] Ação filmável, no presente; nenhum pensamento sem imagem.
- [ ] Falas curtas, com intenção, no idioma do vídeo (tradução ao lado se não for português).
- [ ] Entradas, saídas, portas, objetos, luz e posições coerentes de cena para cena.
- [ ] Personagens pelo comportamento; da aparência, só o que a trama exige.
- [ ] As locações do roteiro são as do universo, com os mesmos nomes.
- [ ] Cenas de alto risco marcadas, cada uma com saída.
- [ ] Notas de direção como sugestão; nenhum prompt, lente ou aparência.
- [ ] Funciona sem som, se for para redes.

## Fontes
Ofício de roteiro (referências clássicas):
- Lajos Egri, *The Art of Dramatic Writing* (1946): premissa.
- Robert McKee, *Story* (1997): ideia controladora; a cena como mudança de valor.
- Syd Field, *Screenplay* (1979): estrutura e pontos de virada.
- "Arma de Tchekhov": plantar e pagar.
- Cabeçalho INT./EXT. e personagem em maiúsculas: formato padrão do roteiro de cinema.

Continuidade em vídeo de IA (pesquisa do Orquestrador em 2026-10-04, feita por trechos de busca):
- O modelo não guarda a posição da câmera entre gerações; cada clipe precisa declarar de novo a direção e a geografia: https://hackernoon.com/ai-video-generation-forgets-where-the-camera-was-heres-the-screen-direction-workflow-that-fixes-it (2026, terceiro, confiança média).
- Falhas relatadas no Seedance 2.5: https://www.kapwing.com/resources/is-seedance-2-5-actually-better-than-2-0-heres-what-i-found/ (ago. a set. de 2026, terceiro, confiança baixa).
- Modelos de vídeo entendem pouco de física: https://arxiv.org/pdf/2501.09038 (jan. de 2025, confiança média).

Se a ferramenta mudou, peça ao pilar skills a atualização.

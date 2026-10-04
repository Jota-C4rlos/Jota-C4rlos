---
name: suno
description: Guia do Orquestrador para o Suno v6 - modelos e planos, modo Advanced, campos Style e Lyrics, metatags de estrutura, instrumental, Variety, duração, edição (Extend, Cover, Replace Section, Voices) e direitos de uso comercial e downloads; com os modelos de prompt de estilo e de letra e como encaixar a música num vídeo de 15 a 60 s. Use em todo prompt de música do pilar musica quando a ferramenta for o Suno (padrão).
user-invocable: false
---
# Suno v6

Situação em 2026-10-04: a família v6 é o modelo atual da Suno desde 09/09/2026. Todos os modelos anteriores (v4 a v5.5) foram aposentados: as músicas antigas continuam na biblioteca, mas toda nova iteração delas sai em v6. Guias de prompt escritos para v4.5, v5 e v5.5 estão desatualizados: não use truques deles sem testar.

O José gera, no site ou no app. O pilar musica escreve a configuração, o Style (em inglês, com a tradução), a letra (no idioma do vídeo) e o nome de cada arquivo. O ouvido é do José.

## 1. Modelos e planos
| Modelo | O que é | Quem usa |
|---|---|---|
| v6 | principal | Pro e Premier |
| v6-wild | experimental | Pro e Premier |
| v6-mini | rápido e grátis | todos, inclusive o Free |

- Uma geração vai até 8 minutos, nos três. Para mais, Extend.
- No Orquestrador: v6 para a faixa que vai ao vídeo. v6-wild só numa variação declarada como experimental. v6-mini serve de rascunho; música feita no Free é só para uso pessoal (seção 7).
- Segundo a Suno, o v6 entende melhor a linguagem de músico (vocais, instrumentação, estrutura, clima e referências): escreva o Style como um músico descreveria o arranjo.

## 2. Modos de criação
A confirmar: a descrição da tela vem de guias de terceiros.
- **Simple**: linguagem natural e referências (músicas da Suno, playlists, áudio enviado, imagens e vídeo). Tem o botão Instrumental.
- **Advanced**: campos explícitos (Style, Lyrics), Vocal Gender, Duration Custom/Auto, Max Mode e os controles Weirdness, Style Influence (padrão 50%) e Variety (novo, padrão Normal).
- **Sounds**: efeitos, loops e one-shots.

No Orquestrador, trilha e canção são sempre no Advanced: campos explícitos dão controle. Sounds pode servir para um efeito ou um golpe curto (sting), se o José quiser.

## 3. Configuração padrão (Advanced)
| Controle | Valor no Orquestrador | Por quê |
|---|---|---|
| Modelo | v6 | faixa final, no Pro ou no Premier |
| Instrumental | ligado na trilha; desligado na canção | sem ele, a Suno pode cantar |
| Vocal Gender | o do conceito, na canção | — |
| Duration | Custom: vídeo + 2 a 4 s | é um alvo, não uma garantia |
| Variety | 0 | regra oficial: só em 0 os style tags ficam como escritos; ligado, a Suno reescreve o Style |
| Style Influence e Weirdness | padrão | mude só depois de testar, e anote no caderno |
| Max Mode | desligado em vídeo curto | custa o dobro; vale para música acima de 2 min, cover e consistência de voz |
| Exclude Styles | o que não pode aparecer (ex.: vocals, piano) | a confirmar se continua no v6 |

Duration: chegou à web em 20/07/2026 (v5.5), com alvo de até 6 min, e continua no Advanced do v6. A faixa de valores (uma API não oficial diz 10 a 360 s) e a precisão em alvos curtos estão a confirmar.

## 4. Campo Style (inglês)
Limite: cerca de 1.000 caracteres (a confirmar; só terceiros confirmam para o v6). Na prática, 1 a 3 linhas bastam.

Ordem, em frases curtas separadas por vírgula:
`<gênero e subgênero>, <clima em 2 ou 3 palavras>, <instrumentação principal>, <voz com tipo e idioma | instrumental>, <produção>, <NN> BPM, <tom>`

- BPM e tom em texto simples, no fim ("120 BPM, D minor"). É prática de guias de terceiros: o número ancora melhor que "medium tempo", mas é alvo, não trava. Groove e bateria em half-time ou double-time mudam o andamento percebido. A obediência ao tom não foi testada: a confirmar.
- Voz cantada: diga o idioma ("warm male vocal in Brazilian Portuguese").
- Nunca nome de artista, banda, música ou marca: descreva época, instrumentos, produção e clima.
- Palavra concreta vence adjetivo vazio: "felt piano, taiko hits" diz mais que "epic, amazing".
- Conte os caracteres antes de entregar: `printf '%s' "<style>" | wc -m`.

Exclude Styles (se existir no v6): a lista do que não pode entrar; na tela, cada item aparece com "-" na frente (ex.: -piano). Use para tirar a voz da trilha ou um instrumento que insiste em aparecer.

## 5. Campo Lyrics
Limite: cerca de 5.000 caracteres (a confirmar). Letra no idioma do vídeo.

Metatags de estrutura (glossário oficial), cada uma na sua linha, entre colchetes:
- Seções: [Intro], [Verse], [Pre-Chorus], [Chorus], [Post-Chorus], [Bridge], [Outro].
- Instrumentais: [Instrumental], [Instrumental Break], [Guitar Solo], [Piano Solo], [Drum Solo], [Bass Solo].
- Da comunidade, fora do glossário (a testar no v6): [End] para encerrar sem cauda; [Break] para pausa ou tensão.

Do mapa de seções para as tags (sugestão do Orquestrador):
| Seção do mapa | Tag |
|---|---|
| Gancho | [Intro] curta, ou começar direto no [Chorus] |
| Mundo, desenvolvimento | [Verse] |
| Escalada | [Pre-Chorus] |
| Parada de 1 batida | [Break] (a testar) |
| Pico | [Chorus] |
| Trecho sem voz (fala, virada) | [Instrumental Break] |
| Resolução | [Outro] e depois [End] |

- Tudo o que não está entre colchetes tende a ser cantado (heurística): não escreva instruções soltas na letra.
- Escreva como se fala no Brasil. Palavra difícil de cantar, troque.
- Trilha instrumental: toggle Instrumental ligado, ou Lyrics vazio. Escrever só as tags com o toggle ligado, para guiar a estrutura: a testar. Se o Suno ignorar, deixe vazio e confie no Style.
- Numa canção, [Instrumental] ou [Instrumental Break] abrem espaço para uma fala do vídeo.

## 6. Encaixar num vídeo de 15 a 60 s
O Suno não recebe marcas de tempo: o encaixe vem do BPM, do tamanho de cada seção e da edição.
1. BPM do mapa no fim do Style; Variety em 0.
2. Poucas seções, na ordem do mapa (tabela abaixo).
3. Duration Custom = vídeo + 2 a 4 s; feche com [Outro] e [End].
4. O José ouve e escolhe. O ajuste fino é na edição: deslizar a faixa para o pico cair no corte, aparar e fazer fade no fim. Desalinhamento de 20 a 50 ms já se percebe em som de percussão (terceiro, confiança baixa).
5. Plano B: gerar mais longo (Duration Auto) e cortar na edição o trecho que serve. Funciona bem na trilha instrumental.

| Vídeo | Duration | Estrutura (canção) | Linhas de letra |
|---|---|---|---|
| 15 s | 17 a 19 s | [Intro] curta · [Chorus] · [End] | 2 a 4 |
| 30 s | 32 a 34 s | [Intro] · [Verse] · [Chorus] · [Outro] · [End] | 6 a 8 |
| 60 s | 62 a 64 s | [Intro] · [Verse] · [Pre-Chorus] · [Chorus] · [Instrumental Break] · [Chorus] · [Outro] · [End] | 12 a 16 |

As linhas de letra são estimativa a testar: a 120 BPM, uma linha cantada leva cerca de 1 a 2 compassos (2 a 4 s). Anote no caderno o que o Suno fez.

## 7. Direitos e downloads (prioridade)
Regras oficiais:
- **Free**: só uso pessoal, não comercial; não pode monetizar (YouTube incluído); a Suno mantém a propriedade. Assinar depois não dá direito retroativo às músicas feitas no Free.
- **Pro e Premier**: uso comercial (Spotify, Apple Music, YouTube, TikTok); o direito continua depois de cancelar a assinatura.
- **Desde 03/09/2026**: uso comercial só para música baixada pelo canal oficial da Suno, dentro da cota do plano pago. Gravar a tela ou capturar o áudio de outro jeito é proibido. O direito de um download permitido é perpétuo: não some se a cota acabar, o preço mudar ou a assinatura vencer.
- **Cota de downloads**: Free 7 na vida (só uso pessoal), Pro 20 por mês, Premier 60 por mês. Não acumula; zera na data de cobrança. Uma música conta 1 download, em qualquer formato e quantas vezes for baixada. Dá para comprar downloads extras. No Premier, o fluxo do Suno Studio não tem limite. Vale para a biblioteca toda, inclusive músicas antigas.
- **Remix**: remixar música de outra pessoa nunca é comercial. Música própria: o Remix FAQ diz que vale se a original e o remix foram feitos com assinatura ativa, mas os termos de 03/09 falam em Remix não comercial "regardless of tier". Extend e Cover de música própria: a confirmar. Por isso, prefira a duração completa numa geração só.
- **Anúncio pago** é uso comercial: Pro ou Premier, e download oficial.
- O treino do v6 com catálogos licenciados (Warner, BMG e Believe/TuneCore, segundo a imprensa) não muda essas regras.

No Orquestrador: o José ouve no app e baixa só a escolhida (ou as finalistas), porque cada download gasta a cota. Cada faixa baixada vira uma linha em 06_Musica/registro-faixas.md.

Preços e créditos, segundo terceiros (a confirmar em suno.com/pricing): Pro US$ 10/mês (US$ 8 no anual), 2.500 créditos; Premier US$ 30/mês (US$ 24 no anual), 10.000 créditos e o Suno Studio. Geração normal: 10 créditos para 2 músicas; com Max Mode, 20. Prompt com muitas imagens ou vídeos custa mais.

## 8. Edição e recursos extras
- **Edição de letra e de seção** por linguagem natural, sem regerar tudo: trocar uma palavra ou uma linha, ou pedir algo como "change the chorus so it's sung by a gospel choir" (confiança média).
- **Replace Section** (Pro e Premier): regera um trecho de 10 a 30 s e devolve 2 versões. Bom para consertar o pico sem perder o resto.
- **Extend** continua do ponto escolhido; "Get Whole Song" junta original e extensão. **Cover** refaz a música em outro estilo. Cover, Extend, Reuse e Speed ficam no menu Remix/Edit: vale a regra de Remix.
- **Voices** (o antigo Personas, desde o v5.5): clona a voz cantada do próprio usuário, com verificação por frase falada, só para maiores de 18 anos; Pro e Premier, com teste no Free. Só se o José quiser cantar com a voz dele. Custom Models (Pro e Premier) treina com pelo menos 6 faixas próprias.
- **Suno Studio** (Premier; Studio 2.0 desde 13/08/2026): DAW no navegador, com MIDI, separação de stems e efeitos; exporta stems sem gastar downloads (terceiros). Útil para tirar a melodia sob uma fala.
- **Referências** (áudio, imagem, vídeo): não está claro se o vídeo é analisado ou se só o áudio dele é extraído (confiança baixa). Nunca envie música de terceiros como referência.
- **Suno Speech** (beta, 01/10/2026): narração e trilha juntas numa faixa. Experimento para histórias narradas; a imprensa relata sotaque oscilando e pausas longas.

## 9. Modelo do bloco de prompts (vai no musica_vNN.md)
````markdown
## Prompts — Suno v6 (Advanced)
Configuração: v6 · Advanced · Instrumental: ligado · Duration: Custom 33 s · Variety: 0 · Max Mode: desligado · Weirdness e Style Influence: padrão
Ouça no app e baixe só a escolhida, pelo botão oficial (cada download gasta a cota do mês).

### Variação A — pulso (recomendada: o conceito como está)
Title: porta-pulso
Style (EN, 203 caracteres):
```
cinematic electronic suspense, tense and driving, ticking analog synth arpeggio, deep sub bass, taiko hits, muted felt piano, instrumental, wide modern mix, tight low end, no long intro, 120 BPM, D minor
```
Tradução: suspense eletrônico de cinema, tenso e com pulso, arpejo de sintetizador analógico em tique-taque, grave sub profundo, golpes de taiko, piano de feltro abafado, instrumental, mixagem moderna e aberta, grave firme, sem intro longa, 120 BPM, Ré menor.
Exclude Styles: vocals, choir (se o campo existir no v6)
Lyrics: vazio. Teste opcional: só as tags [Intro] [Verse] [Pre-Chorus] [Break] [Chorus] [Outro] [End].
Salvar como: 06_Musica/faixas/musica-pulso_01.mp3 e musica-pulso_02.mp3 (cada versão baixada ganha o próximo número)

### Variação B — orquestra (muda a instrumentação; mesmo mapa e BPM)
Style (EN, 184 caracteres):
```
orchestral hybrid suspense, tense then triumphant, staccato low strings, deep taiko ensemble, brass swells, ticking clock percussion, instrumental, cinematic wide mix, 120 BPM, D minor
```
Tradução: suspense orquestral híbrido, tenso e depois triunfante, cordas graves em staccato, conjunto de taikos graves, metais que crescem, percussão de relógio, instrumental, mixagem larga de cinema, 120 BPM, Ré menor.
Salvar como: 06_Musica/faixas/musica-orquestra_01.mp3 e musica-orquestra_02.mp3
````

Canção curta (vídeo de 15 s, letra em português):
```
Style: bright Brazilian pop, warm and hopeful, acoustic guitar, light percussion, hand claps, warm male vocal in Brazilian Portuguese, clean modern mix, 120 BPM, G major
Lyrics:
[Intro]
[Chorus]
Abre a porta, deixa entrar
tudo o que a gente veio buscar
[Outro]
[End]
```
Tradução do Style: pop brasileiro luminoso, caloroso e esperançoso, violão, percussão leve, palmas, voz masculina calorosa em português do Brasil, mixagem moderna e limpa, 120 BPM, Sol maior.

## 10. Diagnóstico rápido
| Problema | Ajuste |
|---|---|
| O estilo saiu diferente do escrito | Variety em 0; gênero primeiro; menos adjetivos, mais instrumentos |
| Intro longa, gancho atrasado | [Intro] curta ou começar no [Chorus]; "no long intro" no Style (a testar); cortar o começo na edição |
| A música não termina, ou a cauda é longa | [Outro] e [End]; Duration = vídeo + 2 a 4 s; fade na edição |
| Veio voz na trilha | toggle Instrumental; "instrumental" no Style; Exclude Styles: vocals |
| Andamento diferente do pedido | BPM no fim do Style; nada de "half-time"; ajuste fino na edição |
| Palavra cantada errada | escrever como se fala; trocar só a palavra pela edição de letra |
| O pico não cai no corte | deslizar a faixa na edição; Replace Section no trecho |
| Duração muito longe do alvo | plano B: gerar mais longo e cortar |

## 11. A confirmar
| O quê | Como confirmar |
|---|---|
| Limites do Style (1.000), do Lyrics (5.000) e do título (80 ou 100) | o José cola um texto longo e vê onde o campo para; o pilar skills lê a página oficial |
| Faixa e precisão do Duration Custom em 15 a 60 s | o José gera um teste de 20 s; a musica mede com ffprobe |
| Exclude Styles no Advanced do v6 | o José abre a tela e conta |
| Tags no Lyrics com o toggle Instrumental ligado; [End] e [Break] no v6 | um teste curto |
| Obediência ao BPM e ao tom | o José confere num app de BPM (tap tempo) e anota |
| Extend e Cover de música própria em uso comercial | o pilar skills lê os termos e o Remix FAQ; na dúvida, não use em material comercial |
| Preços, créditos e preço do download extra | suno.com/pricing; registrar em _Sistema/ferramentas-e-contas.md, com data |
| Se a entrada de vídeo analisa a imagem | a doc oficial ou um teste |

Como confirmar: o José testa e conta o que viu; a musica anota no caderno; o pilar skills confere na doc oficial e atualiza esta skill.

## Fontes
Pesquisa do Orquestrador em 2026-10-04, por trechos de busca (as páginas não puderam ser abertas):
- Família v6 e planos: https://help.suno.com/en/articles/13924737 (09/09/2026).
- v6 FAQ (aposentadoria dos modelos antigos, Variety, Max Mode): https://help.suno.com/en/articles/13924481 (set. 2026).
- Duração máxima de 8 min: https://help.suno.com/en/articles/13924929 (set. 2026).
- Controle de duração: https://suno.com/release-notes/duration-slider-on-web (20/07/2026, confiança média).
- Limites dos campos, BPM e tom no Style: https://hookgenius.app/learn/suno-v6-guide/ (set. 2026, terceiro, confiança média e baixa).
- Modos e controles do v6: https://jackrighteous.com/en-us/blogs/guides-using-suno-ai-music-creation/inside-suno-v6-create-simple-advanced-sounds-guide (set. 2026, terceiro, confiança média).
- Edição de letra e de seção: https://help.suno.com/en/articles/13924801 (set. 2026, confiança média).
- Metatags: https://help.suno.com/en/articles/9010177 (sem data visível).
- Instrumental: https://help.suno.com/en/articles/3726721 (sem data visível, confiança média).
- Exclude Styles: https://suno.com/release-notes/exclude-styles (2025, anterior ao v6, confiança média).
- Voices, Custom Models e My Taste: https://help.suno.com/en/articles/11362369 (26/03/2026, confiança média).
- Extend, Cover e Replace Section: https://help.suno.com/en/articles/3271873 (sem data visível).
- Suno Studio: https://usesuno.com/features (set. 2026, terceiro, confiança média).
- Cota de downloads: https://help.suno.com/en/articles/13926209 (03/09/2026).
- Direitos por plano: https://help.suno.com/en/articles/9601601 (sem data visível; reconfirmado nas regras de set. 2026).
- Termos novos: https://suno.com/blog/suno-updates-tos (ago. a set. 2026).
- Remix FAQ: https://help.suno.com/en/articles/5663873 (sem data visível, confiança média).
- Preços: https://techjacksolutions.com/ai-tools/suno/suno-pricing/ (2026, terceiro, confiança média).
- Referências de áudio, imagem e vídeo: https://jackrighteous.com/en-us/blogs/guides-using-suno-ai-music-creation/inside-suno-v6-audio-uploads-references-guide (set. 2026, terceiro, confiança baixa).
- Suno Speech: https://www.suno.com/release-notes/introducing-speech-beta (01/10/2026, confiança média).
- Treino licenciado do v6: https://thenextweb.com/news/suno-v6-warner-bmg-believe-licensed-models (set. 2026, imprensa, confiança média).
- Sincronia percebida: https://beatsyncpro.ai/blog/how-to-sync-video-to-music.html (2026, terceiro, confiança baixa).

Se a ferramenta mudou, peça ao pilar skills a atualização.

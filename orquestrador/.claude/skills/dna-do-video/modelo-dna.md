# Modelo do DNA do vídeo

Copie o bloco abaixo para `Box_de_Ideias/dna/dna_<ref-id>.md` e preencha. Campo sem dado fica "—"; nunca invente. No frontmatter, `data` é o dia da análise. As listas de apoio estão no fim deste arquivo.

Marcação: o que foi medido no arquivo, lido na página ou informado pelo José é fato e vai sem marca. Interpretação sua leva "(hipótese)". Evidência dos momentos: **A** sinal externo (métrica, "Mais repetidos" do YouTube, comentários que citam o momento) · **B** medido no vídeo (corte, pico ou queda de volume, fala, texto novo, evento sonoro) · **C** inferido dos frames (hipótese).

````markdown
---
id: ref-NNN
data: AAAA-MM-DD
fonte: <link ou caminho do arquivo>
plataforma:
perfil:
categoria:
analise: completa | parcial (só link) | parcial (sem transcrição)
---
# DNA — <título curto do vídeo>

## 1. Ficha técnica
| Campo | Valor | Fonte |
|---|---|---|
| Link ou arquivo | | |
| Perfil e data de publicação | | página ou José |
| Idade do post na análise | | |
| Duração · proporção · resolução · fps | | probe.json |
| Áudio | sim ou não | probe.json |
| Planos · duração média de plano · cortes por segundo | | cortes.txt (limiar 0.30) |
| Primeiro corte · cortes em 0-3 s · em 0-5 s · máx. de planos em 5 s | | cortes.txt |
| Primeira palavra · palavras por segundo · % do tempo com fala | | transcrição |
| Som usado (nome, se a página informar) | | página |
| Picos de volume (tempo e LUFS) | | loudness.txt |
| Silêncios | | silencios.txt |
| Transcrição feita com | faster-whisper turbo, Scribe v2, legenda da plataforma ou — | |

## 2. Resumo
- O que acontece, em 1 frase:
- Formato:
- Promessa ao espectador e tempo até a promessa (s):
- Por que viralizou, em 2 linhas (hipótese):

## 3. Momentos de viralização
| tempo | o que acontece | por que prende | gatilho | tipo | força 1-5 | evidência |
|---|---|---|---|---|---|---|
| 00:01.2 | a porta abre sozinha antes de a mão tocar | quebra a expectativa no 1º segundo (hipótese) | surpresa | gancho | 5 | B: corte + pico de volume |

De 3 a 7 momentos, em ordem de tempo.
Trechos de risco, onde a pessoa pode sair (mais de 2 a 3 s sem mudança de imagem ou som, preparação antes da promessa, CTA cedo, queda de energia na fala):

## 4. Gancho (0 a 3 s)
- Tipo:
- Imagem (o 1º frame e o que muda até 1 s):
- Fala (literal, com tempo):
- Texto na tela:
- Som:
- Tempo até a promessa:
- Força do gancho 1-5 e por quê:

## 5. Transcrição com tempos
[00:00.0–00:01.8] fala, como saiu da transcrição
[00:02.1] (risada) — evento sonoro, se houver
Fala literal serve à análise; não vai para roteiro nosso.

## 6. Estrutura em batidas
| # | início–fim | duração | imagem (frame) | fala | texto na tela | som | função | recurso de retenção |
|---|---|---|---|---|---|---|---|---|
| 1 | 00:00.0–00:01.5 | 1,5 s | corte_001 | | | | gancho | |

Loops abertos: onde abre, onde fecha, a distância em segundos. O final emenda no começo (replay)?

## 7. Ritmo
- Planos, duração média de plano, cortes por segundo:
- Cortes por janela de 5 s (0-5, 5-10...):
- Os cortes caem nos picos do áudio ou na batida da música?
- Onde acelera e onde respira:

## 8. Texto na tela
Presença, quando entra, se acompanha a fala, tamanho e posição (dentro da área segura), legendas, emoji.

## 9. Áudio
- Música: original ou som em alta (trend); nome, se a página informar; drop em (s):
- Voz: narração, fala para a câmera ou diálogo; idioma; ritmo:
- Efeitos sonoros (SFX):
- Silêncios e picos usados como recurso:

## 10. Visual
Enquadramentos (close, médio, aberto; câmera na mão ou fixa; olhar para a câmera), movimento de câmera (hipótese, visto entre frames), cor e luz, estética (UGC, cinematográfica, 2D, pixel, hiper-realista...).

## 11. Personagens e formato
Quem aparece, como age e fala, persona comum ou ator. Formato (lista no fim).

## 12. CTA
Falado, em texto ou os dois; o tipo (comprar, link na bio, comentar, salvar, parte 2, seguir); em que segundo aparece.

## 13. Métricas
| Métrica | Valor | Fonte (José ou página) | Data |
|---|---|---|---|
Razões, quando houver os números: compartilhamentos/views, salvamentos/views, comentários/views, curtidas/views.
Sem métrica: escreva "sem métrica informada".
Comentários: só os temas e os momentos citados, sem @ nem nomes.

## 14. Notas por critério
Marcas objetivas (sim ou não, com o tempo):
| Marca | Critério | Resultado |
|---|---|---|
| Attract | início dinâmico: o 1º plano muda em menos de 3 s | |
| Attract | ritmo rápido: 5 ou mais planos em alguma janela de 5 s | |
| Attract | ritmo rápido no início: 5 ou mais planos nos 5 s iniciais | |
| Attract | ritmo geral: duração média de plano abaixo de 2 s | |
| Attract | áudio cedo: fala ou narração nos 5 s iniciais | |
| Attract | texto na tela; texto sincronizado com a fala | |
| Brand | marca ou produto nos 5 s iniciais (fala, texto ou imagem) | |
| Connect | pessoa ou personagem presente; rosto visível nos 5 s iniciais | |
| Direct | CTA falado; CTA em texto | |

Notas de 1 a 5:
| Critério | Nota | Por quê (com tempo) | Evidência |
|---|---|---|---|
| Attract (atrai) | | | |
| Brand (marca) | | | |
| Connect (conecta) | | | |
| Direct (direciona) | | | |
| Retenção | | | |
| Emoção | | | |
| Compartilhamento | | | |
| Replicabilidade | | | |

## 15. O que aproveitar (princípios, não cópia)
| Princípio | Onde aparece (tempo) | Como vira trabalho nosso | Pilar |
|---|---|---|---|
| gancho com imagem impossível em 0-1 s | 00:00.0 | primeiro quadro do storyboard e take 1 | visual, prompts |
| drop da música colado no primeiro corte | 00:02.0 | marcar o drop no plano musical | musica |

Não copiar: <falas, personagens, imagens, música, marca deste vídeo>.

## 16. Ideias derivadas
| id | título | em uma frase | princípio que usa |
|---|---|---|---|
Cada uma tem nota própria em Box_de_Ideias/ideias/ com status "sugerida".

## 17. Limitações desta análise
- Frames amostrados a <N> por segundo e um por corte; movimento entre amostras pode ter escapado.
- Transições suaves (fusões) podem não ter sido contadas como corte.
- Transcrição automática; erra mais em letra cantada e com música alta.
- <só link: sem frames nem áudio medido> · <outras>

Arquivos de trabalho: Box_de_Ideias/dna/<ref-id>/ (probe.json, cortes.txt, audio_16k.wav, silencios.txt, loudness.txt, transcricao.json, frames/)
````

## Listas de apoio

**Formatos**: talking head ou UGC, POV, tutorial, antes e depois, esquete, storytime, lista, unboxing, ASMR ou satisfatório, green screen, slideshow, cinematográfico IA.

**Tipos de gancho**: pergunta ou curiosidade · afirmação ousada ou contraintuitiva · aviso ("pare de...") · resultado primeiro, antes e depois · POV ou identificação · quebra de padrão visual (movimento, zoom, objeto inesperado) · começo no meio da ação · dor ou problema · número ou lista · desafio ou prova · autoridade ou prova social · humor ou absurdo.

**Funções das batidas**: gancho, preparação, loop aberto, escalada, re-gancho, recompensa (payoff), virada, CTA, loop final.

**Recursos de retenção**: corte seco, punch-in (zoom de corte), troca de ângulo, b-roll, legenda dinâmica, contagem, revelação, efeito sonoro, silêncio antes do pico.

**Tipos de momento**: gancho, revelação ou recompensa, virada, punchline, momento compartilhável ("print"), momento de comentário ou polêmica, demonstração ou prova, ponto de loop, CTA.

**Gatilhos**: surpresa, humor, identificação, curiosidade, medo de ficar de fora, indignação, inspiração, satisfação (ASMR), nostalgia, fofura, tensão.

**Força do momento (1 a 5)**
1. Detalhe que ajuda pouco.
2. Sustenta a atenção.
3. Momento claro de retenção (re-gancho, virada pequena).
4. Provável causa de replay, comentário ou compartilhamento.
5. O motivo central da viralização: sem ele, o vídeo não funciona.
Evidência A ou B pesa mais que C. Força 5 só com evidência A ou B.

**Força do gancho (1 a 5)**: 1 genérico, ou a promessa só chega depois de 3 s · 2 claro, mas comum · 3 claro e com um elemento novo · 4 promessa clara e novidade visual até 1,5 s · 5 várias camadas juntas (imagem, fala e texto) com curiosidade em até 1 s.

**Notas por critério (1 a 5)**: 1 fraco ou ausente · 2 presente, sem força · 3 comum e bem feito · 4 acima da média, com um recurso claro · 5 exemplar, vale estudar.
- Attract: o quanto segura nos primeiros segundos (início dinâmico, ritmo, gancho).
- Brand: marca ou produto presente cedo e bem integrado. Vídeo sem marca: avalie a assinatura do criador (personagem, estilo ou bordão reconhecível) e escreva "adaptado".
- Connect: pessoas ou personagens, rosto, olhar para a câmera, identificação.
- Direct: CTA claro, falado ou em texto, e oferta.
- Retenção: estrutura, loops abertos, re-ganchos, recompensa, sem trecho morto.
- Emoção: intensidade e clareza do gatilho.
- Compartilhamento: por que alguém mandaria para outra pessoa (identificação, utilidade, humor, polêmica); use as razões das métricas quando houver.
- Replicabilidade: quanto do DNA dá para levar ao nosso fluxo (Midjourney, Seedance ou Kling, Suno ou ElevenLabs) sem copiar.

**Sinais de Shorts (opcional)**: sujeito ocupando 60% ou mais do quadro, olhar direto para a câmera, voz humana, linguagem casual, humor, personagem com transformação, estética UGC ou "nativa", texto com emoji, 9:16 sem tarja. Em história 100% IA, adapte: voz humana vira narração; olhar para a câmera vira personagem encarando a câmera; UGC vira câmera na mão simulada no prompt.

As marcas ABCD seguem os critérios do ABCDs Detector (repositório da Google Marketing Solutions, que avisa não ser um produto oficial do Google). As âncoras das notas são do Orquestrador: depois de 10 a 20 DNAs, compare as notas com as razões compartilhamentos/views e salvamentos/views e peça ao pilar skills o ajuste.
Fontes: https://github.com/google-marketing-solutions/abcds-detector (2026-07-01) e features_repository/shorts_features.py no mesmo repositório (2026-07-01).

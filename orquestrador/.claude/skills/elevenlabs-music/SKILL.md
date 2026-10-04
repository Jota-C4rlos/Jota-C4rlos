---
name: elevenlabs-music
description: Guia do Orquestrador para o ElevenLabs Music v2.5 - onde gerar (ElevenMusic, plataforma ou API), duração, prompt com marcas de tempo, plano de seções (composition plan) com a duração de cada trecho casada com os cortes do vídeo, instrumental, BPM e tom, inpainting, referência de áudio, Video to Music, idiomas e licença por plano. Use quando a ferramenta de música escolhida for o ElevenLabs (alternativa ao Suno), sobretudo quando a trilha precisa cair no segundo exato dos cortes.
user-invocable: false
---
# ElevenLabs Music v2.5

Situação em 2026-10-04: o Music v2.5 (11/09/2026) é o modelo atual da ElevenLabs. É o padrão no ElevenMusic, para geração por prompt e por referência, e no API usa o model_id `music_v2_5`. Está também no ElevenCreative, no Studio e nos Flows.

Linha do tempo: Eleven Music v1 (05/08/2025) → Music v2 (27/05/2026: troca de gênero no meio da faixa, edição por seção, rap rápido, multilíngue melhor) → v2.5 (instrumentos mais naturais, arranjos mais ricos, melhor aderência ao prompt).

O José gera. O pilar musica escreve o prompt (em inglês, com a tradução), o plano de seções no tempo do vídeo, a letra (no idioma do vídeo) e o nome de cada arquivo. O ouvido é do José.

## 1. Quando usar
- A trilha precisa cair no segundo exato dos cortes: o plano de seções dá a duração de cada trecho em milissegundos, e o v2/v2.5 sempre respeita essas durações.
- Segundo o guia oficial, o modelo segue o BPM com precisão e costuma acertar o tom (confiança média: confira no primeiro teste).
- Canção com identidade de "música" (refrão, voz marcante): o Suno tende a ser a escolha (recomendação da pesquisa). A decisão é do José, pela linha MÉTODO.

## 2. Onde gerar
| Onde | O que é | Planos |
|---|---|---|
| ElevenMusic | app de consumo (iOS desde abril de 2026, e web) | planos próprios (seção 9) |
| Plataforma ElevenLabs | Music dentro da plataforma (Studio, ElevenCreative, Flows) | Free, Starter, Creator, Pro, Scale, Business, Enterprise |
| API | endpoint compose, model_id `music_v2_5` | só planos pagos (terceiros: a partir do Starter; a confirmar) |

Os termos mudam conforme onde a faixa foi criada: registre o lugar e o plano em 06_Musica/registro-faixas.md. O pilar não chama o API. Se o José quiser usá-lo, a decisão e o gasto são dele, com a chave na variável de ambiente ELEVENLABS_API_KEY.

## 3. Limites
| Item | Valor |
|---|---|
| Duração | 3 s a 10 min. No API, music_length_ms de 3.000 a 600.000 (só na geração por prompt; com plano de seções, vale a soma delas). Na web, duração fixa ou Auto |
| Seções do plano | até 30; cada uma de 3.000 a 120.000 ms; total de 3 s a 10 min |
| Estilos por seção | positive_styles até 50; negative_styles até 50 |
| context_adherence | low, medium ou high (padrão high) |
| Saída no API | output_format "auto" gera mp3_48000_192 nos modelos v2. Formatos superiores dependem do plano (terceiros: MP3 192 kbps a partir do Creator, PCM 44,1 kHz a partir do Pro; a confirmar) |

Guias que ainda falam em limite de 5 min são da época do v1.

## 4. Prompt (geração por prompt)
Pelo guia oficial de boas práticas (confiança média):
- Gênero, clima, instrumentos, voz ou instrumental, BPM e tom em texto ("130 BPM, in A minor").
- Narre o arranjo em ordem, com marcadores de tempo: "start with", "then", "bring in".
- Pistas de tempo explícitas: "lyrics begin at 15 seconds", "instrumental only after 1:45".
- O que não deve tocar também é prompt ("No melody, just drums").
- Instrumental: escreva "instrumental only". No API, some force_instrumental=true (só na geração por prompt). Sem isso, pode vir voz ou não, conforme o prompt.
- Nunca nome de artista, banda, música ou marca: descreva.

Modelo (os tempos vêm do mapa de seções da musica):
```
<genre>, <mood>, <NN> BPM, in <key>. Instrumental only.
Start with <signature sound> from the first second, no intro. At 0:03 <...>. At 0:11 bring in <...>, building every two bars. At 0:20 <turn>. One-beat stop at 0:23.5, then a full hit at 0:24 with <...>. Final hit at 0:28, then ring out and end at 0:33.
```

Exemplo (vídeo de 30 s, 120 BPM):
```
Cinematic electronic suspense, tense and driving, 120 BPM, in D minor. Instrumental only.
Start with a ticking analog synth and a deep sub bass pulse from the first second, no intro. At 0:03 keep it sparse, just the pulse and the sub. At 0:11 bring in taiko drums and a driving bass, building every two bars. At 0:20 hold the tension with sustained low strings. One-beat stop at 0:23.5, then a full hit at 0:24 with taiko, big synth and strings together. Final hit at 0:28, then ring out and end at 0:33. No vocals.
```
Tradução: Suspense eletrônico de cinema, tenso e com pulso, 120 BPM, em Ré menor. Só instrumental. Comece com um sintetizador analógico em tique-taque e o pulso de um grave sub profundo desde o primeiro segundo, sem intro. Aos 0:03, mantenha esparso, só o pulso e o grave. Aos 0:11, entram taikos e um baixo com pulso, crescendo a cada dois compassos. Aos 0:20, segure a tensão com cordas graves sustentadas. Parada de uma batida aos 0:23,5, depois um golpe cheio aos 0:24 com taiko, sintetizador grande e cordas juntos. Golpe final aos 0:28, depois deixe ressoar e termine aos 0:33. Sem voz.

## 5. Plano de seções (composition plan)
É o jeito mais preciso de casar música e cortes. Cada seção ("chunk") tem:
- `text`: o rótulo da seção entre [ ], a letra (se houver) e direções inline entre { }.
- `duration_ms`: de 3.000 a 120.000.
- `positive_styles` e `negative_styles`: o que entra e o que fica de fora naquele trecho (inglês, tags curtas).
- `context_adherence`: low, medium ou high (padrão high).
E `positive_global_styles` para a música toda (gênero, BPM, tom, produção).

Do mapa da musica para o plano:
1. Cada seção do mapa vira uma seção do plano, com duration_ms = duração no vídeo × 1.000.
2. Seção com menos de 3 s não existe: junte-a à vizinha e marque o momento com uma direção inline ({one-beat stop on the last beat}).
3. A soma das seções é a duração da faixa: vídeo + 2 a 4 s, com uma última seção de "final hit, ring out" de pelo menos 3 s.
4. Com o BPM do mapa, cada seção dura um número inteiro de batidas, de preferência de compassos (compasso em ms = 240.000/BPM: 2.000 ms a 120 BPM).
5. positive_styles: a emoção e os instrumentos do trecho. negative_styles: o que atrapalharia ali (vocals sob uma fala, drums na intro).
6. context_adherence: high mantém o trecho ligado ao anterior; low para uma virada brusca, como a troca de gênero que o v2 trouxe. Leitura do Orquestrador: a testar.
7. Letra própria: as linhas vão no text da seção, no idioma do vídeo. Para letra do José, use o plano, não o prompt.

Modelo no musica_vNN.md (mesmo exemplo de 30 s; a parada de 0,5 s entrou na virada e a resolução de 2 s, na cauda):
| # | text | Tempo no vídeo | duration_ms | positive_styles | negative_styles | context_adherence |
|---|---|---|---|---|---|---|
| 1 | [Intro] {signature ticking synth from the first frame} | 00:00–00:03 | 3000 | ticking analog synth, sub bass pulse | long intro, vocals | high |
| 2 | [Verse] | 00:03–00:11 | 8000 | sparse pulse, deep sub bass | melody, vocals, drums | high |
| 3 | [Build] {rises every two bars} | 00:11–00:20 | 9000 | taiko drums, driving bass, rising tension | vocals | high |
| 4 | [Bridge] {hold the tension; one-beat stop on the last beat} | 00:20–00:24 | 4000 | sustained low strings, held tension | drums | high |
| 5 | [Chorus] {full hit on beat one} | 00:24–00:28 | 4000 | full taiko hits, big synth, wide strings | vocals | high |
| 6 | [Outro] {final hit, then ring out} | 00:28–00:33 | 5000 | final hit, long reverb tail | new elements | high |

Total: 33.000 ms (vídeo de 30 s + 3 s de cauda). Globais: cinematic electronic suspense, 120 BPM, D minor, instrumental only, wide modern mix.

Na web: se a tela deixa definir duração e estilos por seção, o José preenche a tabela (a confirmar: o José abre a tela e conta). Se não deixa, use o prompt com marcas de tempo (seção 4), e a tabela orienta a edição.

No API (só por decisão do José), o mesmo plano em JSON:
```json
{
  "positive_global_styles": ["cinematic electronic suspense", "120 BPM", "D minor", "instrumental only"],
  "chunks": [
    {"text": "[Intro] {signature ticking synth from the first frame}", "duration_ms": 3000,
     "positive_styles": ["ticking analog synth", "sub bass pulse"], "negative_styles": ["long intro", "vocals"], "context_adherence": "high"},
    {"text": "[Verse]", "duration_ms": 8000,
     "positive_styles": ["sparse pulse", "deep sub bass"], "negative_styles": ["melody", "vocals", "drums"], "context_adherence": "high"}
  ]
}
```
Os nomes dos campos são os da página Composition plans. Antes de usar, confira nela a estrutura completa (onde vai o model_id, campos obrigatórios). Esquemas com `sections`, `lines` e `positive_local_styles` são do v1: não servem no v2/v2.5.

## 6. Editar sem regerar tudo
- **Inpainting** (v2 e v2.5): regera só um trecho e mantém o resto. Use para consertar o pico ou uma palavra.
- **Audio Reference**: upload de cerca de 30 s para guiar estilo e som; todo upload passa por triagem de copyright. Só material do José (por exemplo, uma faixa aprovada de outro projeto), nunca música de terceiros.
- **Seções de áudio de referência** no plano: inserem um trecho de uma música salva, sem alteração. Servem para manter o gancho aprovado e refazer o resto.

## 7. Video to Music (a confirmar)
- Endpoint POST /v1/music/video-to-music: gera trilha de fundo a partir de um ou mais vídeos. Até 10 arquivos, 200 MB e 600 s no total; descrição opcional de até 1.000 caracteres e style tags. Segundo terceiros, a duração padrão acompanha a do vídeo, e o recurso está no Studio desde agosto de 2025.
- No Orquestrador: atalho com o vídeo já montado. A descrição é o conceito musical em um parágrafo, em inglês; as tags vêm dos estilos globais. Serve só para trilha de fundo e precisa do ouvido do José.
- Isso envia o vídeo do projeto a um serviço externo: o orquestrador avisa o José antes.
- A confirmar: parâmetros exatos, modelo usado (v2 ou v2.5) e plano mínimo.

## 8. Idiomas
- Canta em vários idiomas; o português aparece entre os de qualidade "native-like" (confiança baixa, assim como o total de 59 idiomas). Não há dado sobre o português do Brasil.
- Na canção, ponha "Brazilian Portuguese vocal" nos estilos (heurística) e teste uma variação curta antes da faixa final. Escreva a letra como se fala.

## 9. Licença e planos (a confirmar)
Plataforma ElevenLabs (Eleven Music Model-Specific Terms, confiança média):
- Planos self-serve (Free, Starter, Creator, Pro, Scale, Business): uso comercial online e offline, exceto filme, TV, rádio e Studio Games. O Enterprise cobre todos os usos.
- O acesso gratuito a um modelo de música exige o crédito "Created in collaboration with ElevenLabs", tão visível quanto o texto ao redor. Outra versão dos termos diz que o Free não permite uso comercial nem download: até confirmar, trate o Free como não comercial.
- Reels, Shorts e TikTok monetizados entram em "online commercial".

ElevenMusic, o app (confiança média):
- Free: 5 faixas por dia (há fonte que diz 7); uso comercial com o crédito "Made with ElevenMusic".
- Pro: US$ 9,99/mês (US$ 95,90/ano), 400 faixas por mês (há fonte que diz 500), sem atribuição.
- Os direitos dependem do plano na hora da criação e continuam depois de cancelar. No v2.5, downloads sem perda em todos os planos (terceiros).

API: só planos pagos; os preços divergem entre fontes (confiança baixa).

No Orquestrador: material comercial ou anúncio pago vai em plano pago, sem depender de crédito na tela. TV, cinema ou rádio pedem o Enterprise. Registre onde e com que plano cada faixa foi criada.

## 10. Modelo do bloco de prompts (vai no musica_vNN.md)
````markdown
## Prompts — ElevenLabs Music v2.5
Onde gerar: <ElevenMusic | plataforma ElevenLabs> · Duração: 33 s (soma das seções) · Instrumental: sim ("instrumental only"; vocals em negative_styles)

### Variação A — pulso (recomendada: o conceito como está)
Prompt (EN):
```
(prompt com marcas de tempo, seção 4)
```
Tradução: (fiel, frase a frase)
Plano de seções: (tabela da seção 5, com os estilos globais)
Salvar como: 06_Musica/faixas/musica-pulso_01.mp3 (cada versão baixada ganha o próximo número)

### Variação B — orquestra (muda só a instrumentação; mesmas seções e durações)
(prompt, tradução, estilos que mudam por seção, nome do arquivo)
````

## 11. Diagnóstico rápido
| Problema | Ajuste |
|---|---|
| Veio voz na trilha | "instrumental only" no prompt; vocals em negative_styles; force_instrumental no API |
| A seção mudou cedo ou tarde | conferir duration_ms e a soma até ali; dividir a seção; direção inline no momento |
| Transição brusca demais | context_adherence high na seção seguinte |
| O pico não cai no corte | conferir a soma das durações até o pico; inpainting no trecho; deslizar a faixa na edição |
| Sotaque estranho na letra | "Brazilian Portuguese vocal"; escrever como se fala; testar um trecho curto |
| Seção recusada | menos de 3 s ou mais de 120 s: juntar ou dividir |
| Plano antigo deu erro | esquema do v1 (sections, lines): migrar para chunks |

## 12. A confirmar
| O quê | Como confirmar |
|---|---|
| Se a web deixa editar o plano de seções (duração e estilos por seção) | o José abre a tela e conta |
| Obediência ao BPM e ao tom | o José confere num app de BPM (tap tempo) e anota |
| Português do Brasil na voz | uma variação curta de teste |
| Licença do Free da plataforma; faixas por dia e por mês do ElevenMusic | o pilar skills lê os termos e a central de ajuda; registrar em _Sistema/ferramentas-e-contas.md, com data |
| Video to Music: parâmetros, modelo e plano mínimo | a página do endpoint |
| Planos e preços do API e formatos por plano | elevenlabs.io/pricing/api |

Como confirmar: o José testa e conta o que viu; a musica anota no caderno; o pilar skills confere na doc oficial e atualiza esta skill.

## Fontes
Pesquisa do Orquestrador em 2026-10-04, por trechos de busca (as páginas não puderam ser abertas):
- Music v2.5 e linha do tempo: https://elevenlabs.io/blog/music-v2-5-model (11/09/2026).
- Duração, force_instrumental e formatos: https://elevenlabs.io/docs/api-reference/music/compose (2026).
- Plano de seções (chunks): https://elevenlabs.io/docs/eleven-api/guides/how-to/music/composition-plans (2026).
- Esquema do v1: https://elevenlabs.io/docs/api-reference/music/create-composition-plan (2025 a 2026, confiança média).
- Boas práticas de prompt: https://elevenlabs.io/docs/overview/capabilities/music/best-practices (2026, confiança média).
- Inpainting e Audio Reference: https://elevenlabs.io/docs/eleven-api/guides/how-to/music/inpainting (2026).
- Video to Music: https://elevenlabs.io/docs/api-reference/music/video-to-music (2026, confiança média).
- Idiomas: https://elevenlabs.io/docs/overview/capabilities/music (2026, confiança baixa).
- Licença na plataforma: https://elevenlabs.io/eleven-music-model-specific-terms (2026, confiança média).
- ElevenMusic, planos e direitos: https://help.elevenlabs.io/hc/en-us/articles/46215359714577-Do-I-need-to-pay-to-use-ElevenMusic (2026, confiança média).
- Planos do API: https://elevenlabs.io/pricing/api (2026, confiança baixa).

Se a ferramenta mudou, peça ao pilar skills a atualização.

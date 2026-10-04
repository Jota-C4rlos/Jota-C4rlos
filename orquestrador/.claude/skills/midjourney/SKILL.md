---
name: midjourney
description: Guia do Orquestrador para o Midjourney V8.2 - estrutura e sintaxe do prompt, parâmetros que funcionam e os que não funcionam no V8, consistência de personagem e cenário com o Edit Model e o --sref, fichas (retrato, corpo inteiro, turnaround, expressões), quadros de storyboard e nomes dos arquivos. Use em todo prompt de imagem do pilar visual.
user-invocable: false
---
# Midjourney V8.2

Situação em 2026-10-04: o V8.2 é a versão padrão desde 24/07/2026. Segundo a doc oficial, V8.1 e V8.2 são "99% idênticos"; `--v 8.2` é opcional. O Edit Model do V8 (anunciado em 27/08/2026) substitui o `--cref`, o `--oref` e o Retexture na hora de manter personagens e cenários.

O José gera, no site ou no Discord. O pilar visual escreve os prompts (em inglês, com a tradução em português embaixo), diz o nome de cada arquivo e confere as imagens.

Os modelos de prompt por tipo de imagem (retrato, corpo inteiro, turnaround, expressões, cenário, quadro), com um exemplo completo, estão em .claude/skills/midjourney/modelos-prompt.md: leia antes de escrever as fichas.

Complemento: se a skill da conta anthropic-skills:midjourney estiver disponível, ela aprofunda o fotorrealismo (camadas, câmeras, lentes, film stocks, padrões de luz, pele plástica). Ela foi escrita antes do Edit Model e cobre só fotorrealismo: para referência de personagem, estéticas estilizadas e fichas, vale esta skill.

## 1. Sintaxe (doc oficial)
- Parâmetros sempre no fim, depois de todo o texto. Nada de texto depois deles.
- Espaço antes do `--`. Sem pontuação dentro ou depois dos parâmetros.
- `--ar` sem decimais: `--ar 9:16`, nunca `--ar 0.56:1`.
```
✗ old man at the door--ar 9:16
✗ old man at the door --ar 9:16,
✗ old man --ar 9:16 at the door
✓ old man at the door --ar 9:16
```
- Prompt curto e direto. O V8 é literal: o que você não especifica sai na estética padrão do modelo. Por isso o projeto tem uma âncora de estilo (skill esteticas) e cada personagem e cenário tem um bloco-âncora.
- Para excluir algo, use `--no`. Escrever "sem X" no texto ainda pode gerar X. No máximo 5 itens, e só artefatos que já apareceram.
- Nada de palavras vazias (`4k, masterpiece, hyper-realistic, ultra HD`): descreva luz, material e textura.
- Nunca use nome de estúdio, marca, personagem de terceiros, artista vivo ou pessoa real: descreva as características visuais.
- O nome do personagem não diz nada ao modelo: o prompt descreve, não nomeia.

## 2. Estrutura do prompt
Ordem do Orquestrador:
`[meio] + [sujeito: bloco-âncora] + [ação e pose] + [cenário: bloco-âncora] + [posição na tela] + [luz] + [enquadramento] + [âncora de estilo] + [parâmetros]`
- Hiper-realista: comece pelo sujeito, na ordem Sujeito > Ambiente > Luz > Câmera e lente > Estilo e textura > Parâmetros, com 40 a 90 palavras (padrão da skill anthropic-skills:midjourney).
- Estilizadas (heurística, a testar): comece pelo meio ("2D cel-shaded anime still of ...") e feche com textura, luz e paleta. Teste com e sem `--raw`: ele tira a estética padrão do modelo, o que ajuda a fidelidade e às vezes tira o acabamento ilustrativo.
- Uma imagem, um instante: uma ação por personagem, poses claras.
- Posição na tela: "on the left of frame", "in the background on the right". Lado do corpo: "his left hand" é a mão esquerda do personagem, não a da tela.

## 3. Parâmetros que funcionam no V8.2
| Parâmetro | Faixa e padrão | No Orquestrador |
|---|---|---|
| `--ar W:H` | padrão 1:1; máx. 14:1 (4:1 com --hd) | sempre explícito; quadros na proporção do vídeo |
| `--raw` | liga ou desliga | hiper-realista e claymation; testar nas estilizadas. `--style raw` é sintaxe legada |
| `--s` / `--stylize` | 0–1000, padrão 100 | a faixa da ficha da estética, igual na série toda. Com `--p` ligado, também dosa quanto do perfil entra |
| `--exp` | 0–100, padrão 0; sugeridos 5, 10, 25, 50 | 0 nas séries. Acima de 25–50 atropela `--s` e `--p` e rouba fidelidade às referências |
| `--c` / `--chaos` | 0–100, padrão 0 | 0 nas séries; mais alto só para buscar ideias |
| `--w` / `--weird` | 0–3000 | 0 |
| `--no` | lista curta | até 5 itens, só artefatos já vistos |
| `--seed` | 0–4294967295 | reproduz cerca de 99%, não 100% |
| `--sref` e `--sw` | URL ou código; `--sw` 0–1000, padrão 100 | trava o look da série |
| `--p` | perfil de personalização | o mesmo na série toda, ou nenhum |
| `--hd` | 2048 px direto; 1,3 min de GPU (SD: 0,8) | só na imagem final |
| `--r` | repete o prompt | buscar variações |
| `--tile` | padrão repetível | raro |
| image prompt e `--iw` | imagem no início do prompt; `--iw` pesa imagem contra texto | composição de base |

Moodboards também funcionam no V8.2 (não aceitam `--sw`).

## 4. O que NÃO funciona no V8.x
| Item | Situação |
|---|---|
| `--cref` / `--cw` | só no V6. Substituídos pelo `--oref` no V7 e pelo Edit Model no V8. Guia que ensina `--cref` está obsoleto |
| `--oref` / `--ow` | só no V7. Num prompt V8, o job inteiro rodava em V7 (verificado em agosto de 2026; a confirmar se ainda cai para o V7 ou se agora dá erro). Não use |
| `--q` / `--quality` | não suportado |
| Multi-prompt e pesos `::` (inclusive `--sref URL::2`) | não suportado |
| `--niji` | não compatível; o Niji 7 é uma linha à parte |
| Turbo | não suportado |
| Draft Mode | a doc se contradiz (a tabela diz que não; o artigo do Draft traz dados do V8.1/V8.2): a confirmar testando |

Se um parâmetro for ignorado ou o resultado vier com cara de outra versão, procure no prompt `--oref`, `--cref`, `--q`, `::` ou `--niji`.

## 5. Consistência
Três travas somadas: texto (blocos-âncora), imagem (Edit Model) e estilo (`--sref`, `--p` e os mesmos parâmetros).

### Blocos-âncora
- Personagem: idade aparente, porte, rosto, cabelo, pele, marcas (com o lado do corpo), figurino com cor e material.
- Cenário: lugar, época, 3 a 5 elementos fixos, portas e janelas com posição, regra de luz.
- Copiados palavra por palavra. Nas fichas (retrato, corpo inteiro, turnaround, expressões, cenário) vai o bloco completo.
- Tag curta do personagem (8 a 15 palavras: os traços que o identificam e o figurino da cena), também literal: vai nos quadros que têm o retrato anexado. Texto e imagem se reforçam sem deixar o prompt comprido. Quadro sem referência anexada leva o bloco completo.
- Mudou o figurino numa cena? Troque só a parte do figurino (no bloco e na tag) e registre na tabela "Figurino por cena".
- Varie só a ação, o enquadramento e a posição.

### Edit Model (referências de imagem)
- Aceita até 4 imagens de referência, instrução em texto, inpainting e outpainting. Funciona com o V8.1 e o V8.2.
- A instrução pode ser direta, como numa conversa: "put the man from the portrait reference in the doorway, keep the room unchanged".
- No site: arraste as imagens para a barra de prompt ("attach to prompt"), clique em "edit" no canto inferior direito da imagem aberta ou use a aba "edit" à esquerda. No Discord: `--edit URL`.
- A proporção segue a da PRIMEIRA imagem enviada, a menos que você passe `--ar`. A proporção padrão das configurações não vale aqui. Por isso o `--ar` é sempre explícito.
- Aceita `--p`, moodboards e `--sref`, mas eles podem precisar de mais direção no texto: mantenha a âncora de estilo inteira.
- Até 4 referências por quadro, nesta ordem sugerida: cenário (mestre ou contraplano), rosto do personagem principal, rosto do segundo, corpo inteiro de quem tem figurino importante. Com 3 personagens falta vaga: divida o quadro ou use só o rosto de quem aparece de frente.
- Cite cada referência pelo conteúdo ("the woman from the portrait reference", "the kitchen from the wide reference"). Não achamos sintaxe oficial para "imagem 1, imagem 2": a confirmar.
- Boa referência de personagem (heurística de guias de terceiros, a confirmar): retrato nítido de frente ou em 3/4, luz neutra, fundo liso; corpo inteiro quando silhueta e figurino importam; nada de óculos escuros, rosto coberto, sombra forte, lente distorcida ou maquiagem pesada.
- Para corrigir um detalhe (mão, botão, cor da porta), edite a região em vez de gerar de novo. O changelog do alpha de setembro de 2026 diz que o inpaint e o outpaint passaram a mudar só os pixels selecionados, permitindo edições repetidas sem degradar: a confirmar no site principal.
- Disponibilidade: o anúncio de 27/08/2026 fala em modelo "disponível para teste", e parte das novidades de setembro saiu só no alpha (alpha.midjourney.com). Se a opção de editar não aparecer para o José, use a consistência sem Edit Model (abaixo) e avise o orquestrador.

Sem Edit Model: blocos-âncora idênticos, `--sref` fixo, os mesmos parâmetros, e varie só ação e cenário. A identidade trava menos. O `--oref` só se o José aceitar, sabendo que o job roda em V7 e perde o look do V8.2.

### Estilo travado: `--sref` e `--p`
- O `--sref` aceita a URL de uma imagem ou um código de estilo. `--sref random` sorteia um código e o fixa ao enviar: bom para descobrir o look do projeto; depois, repita o código.
- Não dá para gerar um código a partir de uma imagem sua. Mas a URL de uma imagem aprovada do projeto pode virar o `--sref` da série.
- Com `--sref`, o texto descreve o conteúdo, não instruções: "portrait of an old fisherman", e não "the look of this image but a fisherman". Palavras de estilo só se o estilo não aparecer.
- `--sw` (0–1000, padrão 100) dosa a força do `--sref`. Não funciona com moodboards.
- `--p`: o perfil Global V7 funciona no V8.2; ainda não existe perfil Global V8; perfis V8 não funcionam no V7. Com `--p` ligado, `--s` baixo desliga boa parte do perfil. Ou o projeto inteiro usa o mesmo `--p`, ou nenhum prompt usa.
- O código do `--sref`, o `--p` e os parâmetros da série ficam em estetica_vNN.md.

### Seed
`--seed N` reproduz cerca de 99% no V8. Serve para pequenas variações do mesmo quadro (trocar uma palavra), não como trava de personagem.

## 6. Fichas: ordem de geração
1. Retrato de referência: frente ou 3/4, luz neutra, fundo liso. É a referência principal do rosto.
2. Corpo inteiro: pose neutra, figurino principal completo, fundo liso.
3. Turnaround (opcional: só quando a cena pede; heurística de comunidade, não há doc oficial): frente, 3/4, perfil e costas na mesma imagem. Serve para giros e planos de costas.
4. Expressões (opcional: só quando a cena pede; heurística): 6 expressões do mesmo personagem, as da ficha.
5. Cenário: plano mestre na proporção do vídeo e, para os ângulos que o storyboard usa, contraplano e 2 ou 3 detalhes (a porta, o objeto-chave), na mesma hora e com a mesma luz.

Gere o retrato primeiro. Depois do ✅, anexe-o no Edit Model para o corpo inteiro, o turnaround e as expressões. O mestre aprovado entra como referência do contraplano e dos detalhes.

Nada de texto, rótulos ou setas nas imagens de referência (`--no text, labels`): os guias do Seedance pedem um papel claro para cada referência e avisam para não depender de rótulos escritos na imagem.

## 7. Quadros de storyboard
- `--ar` igual à proporção do vídeo. O Seedance 2.5 aceita 16:9, 4:3, 1:1, 3:4, 9:16 e 21:9; para o Kling, veja a skill do modelo.
- O quadro mostra o instante-chave do plano: composição, posições na tela, luz. Ele vira o primeiro quadro do take ou uma referência dele.
- Referências: as da tabela "Referências aprovadas" do último parecer.
- Quadros seguidos no mesmo cenário: edite o quadro anterior com uma instrução ("move the woman to the window, keep everything else") para manter cenário e luz. Sugestão a testar.
- Primeiro e último quadro do mesmo take: mesmo cenário, mesma luz e o mesmo enquadramento de base. Diferença grande vira corte no vídeo (guia antigo do Kling, a confirmar).
- No Seedance 2.5, os quadros podem entrar em ordem como keyframes de um take com vários planos. Quem escreve isso no prompt de vídeo é o pilar prompts.

## 8. Nomes dos arquivos
O José salva a imagem escolhida da grade em 03_Visual/imagens/, em .png: `<tipo>-<nome>_<NN>.png`. Minúsculas, sem acento, hífen entre palavras; NN é a tentativa salva (01, 02...). Nunca sobrescreva: outra tentativa ganha outro número.

| Imagem | Exemplo |
|---|---|
| Retrato | personagem-ana-retrato_01.png |
| Corpo inteiro | personagem-ana-corpo_01.png |
| Turnaround | personagem-ana-turnaround_01.png |
| Expressões | personagem-ana-expressoes_01.png |
| Plano mestre | cenario-cozinha-mestre_01.png |
| Contraplano | cenario-cozinha-contraplano_01.png |
| Detalhe | cenario-cozinha-detalhe-porta_01.png |
| Quadro do storyboard | quadro-03_01.png |
| Teste de estética | teste-estetica-a_01.png |

## 9. Diagnóstico rápido
| Problema | Ajuste |
|---|---|
| Rosto muda entre imagens | retrato aprovado no Edit Model; bloco-âncora idêntico; baixar `--s` e `--exp`; `--c 0` |
| Estilo muda na série | mesma âncora, mesmo `--sref` ou `--p`, mesmos `--s` e `--raw` |
| Hiper-realista com cara de arte digital | `--raw`, `--s` 50–150, tirar palavras vazias, descrever luz e lente |
| Estilizada saiu semi-real | tirar `--raw`, subir `--s`, abrir o prompt pelo meio |
| Traço assimétrico trocou de lado (cicatriz, relógio, risca do cabelo) | reforçar o lado no texto ("on his left eyebrow") e corrigir editando a região |
| Proporção errada | faltou `--ar`; no Edit Model a proporção vem da primeira imagem |
| Texto, letras ou balões | `--no text, letters, speech bubble` |
| Mãos e dedos | simplificar ou esconder a mão no enquadramento; editar a região |
| Personagem duplicado ou fundido | menos personagens por quadro; posição explícita de cada um na tela |

## 10. A confirmar
- Se o Edit Model já está no site principal para todos, quanto gasta de GPU e se aceita `--raw`, `--seed`, `--exp` e `--hd`.
- Se o `--edit` do Discord aceita várias URLs.
- Se o `--oref` num prompt V8.2 ainda cai para o V7 ou dá erro.
- Pan, Zoom Out e Vary Region rodavam em V6.1, e editar uma imagem HD a rebaixava para SD (agosto de 2026). O changelog de 23/09/2026 (editor com tipos v8.1 e v8.2, canvas em HD) pode ter mudado isso. Até confirmar: faça as edições primeiro e o `--hd` por último.
- Draft Mode no V8.2 (a doc se contradiz).
- Turnaround e folha de expressões: heurísticas de comunidade, sem doc oficial; a confirmar nos testes.
- Nenhum V8.3 ou V9 anunciado oficialmente até 2026-10-04 (só rumor de terceiros).

Como confirmar: o José testa na próxima geração e conta o que viu; o pilar visual anota no caderno; o pilar skills confere na doc oficial e atualiza esta skill.

## Fontes
Pesquisa do Orquestrador em 2026-10-04, feita por trechos de busca (as páginas não puderam ser abertas). Os dados da doc oficial de parâmetros e compatibilidade foram verificados pela skill anthropic-skills:midjourney em agosto de 2026.
- Version (padrão V8.2 desde 24/07/2026; tabela de compatibilidade): https://docs.midjourney.com/hc/en-us/articles/32199405667853-Version (verificado em ago. de 2026)
- Parameter List: https://docs.midjourney.com/hc/en-us/articles/32859204029709-Parameter-List (verificado em ago. de 2026)
- Prompt Basics: https://docs.midjourney.com/hc/en-us/articles/32023408776205 (verificado em ago. de 2026)
- Style Reference: https://docs.midjourney.com/hc/en-us/articles/32180011136653-Style-Reference (verificado em ago. de 2026)
- Omni Reference: https://docs.midjourney.com/hc/en-us/articles/36285124473997-Omni-Reference (verificado em ago. de 2026)
- Legacy Features: https://docs.midjourney.com/hc/en-us/articles/33329788681101-Legacy-Features (sem data visível)
- Edit Model for V8 (anúncio): https://updates.midjourney.com/edit-model-for-v8/ (27/08/2026)
- Edit Model (doc): https://docs.midjourney.com/hc/en-us/articles/48495453462797-Edit-Model (posterior a 27/08/2026)
- Alpha Changelog: https://updates.midjourney.com/alpha-changelog-9-23-26/ (02 a 24/09/2026, confiança média)
- Consistência de personagem no V8, guia de terceiro: https://clipdance.ai/blog/midjourney-v8-character-consistency (2026, confiança baixa)
- Seedance 2.5, proporções, keyframes em ordem e papel de cada referência: https://docs.byteplus.com/en/docs/ModelArk/2607688, https://docs.byteplus.com/en/docs/ModelArk/2607689 e https://www.volcengine.com/activity/seedance25 (jul. e ago. de 2026)
- Kling, primeiro e último quadro: https://kling.ai/quickstart/ai-video-start-end-frames (anterior a 2026, pode estar desatualizado)

Se a ferramenta mudou, peça ao pilar skills a atualização.

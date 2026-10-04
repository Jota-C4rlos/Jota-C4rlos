---
name: continuidade-e-fisica
description: Checklist de continuidade e física dos pilares visual e prompts - mapa da cena (portas, janelas, saídas), direção de tela e regra dos 180°, ordem e posição dos personagens, olhares, figurino e objetos, luz, física, pontes entre takes e erros comuns de vídeo por IA, com a forma de escrever cada regra no prompt e o formato da revisão. Use ao montar cenários e storyboard, ao planejar e revisar takes e ao conferir takes gerados.
user-invocable: false
---
# Continuidade e física

O modelo de vídeo não lembra o take anterior, não guarda a posição da câmera de uma geração para a outra e entende pouco de física. Por isso a continuidade e a física saem certas do papel: do roteiro, do mapa da cena e do prompt. Esta skill é o checklist. Vale para qualquer modelo (Seedance ou Kling).

- **visual (pilar 4)**: o mapa da cena de cada cenário no cenarios_vNN.md; o storyboard com posições, direção de tela e luz coerentes; as imagens conferidas contra o mapa (a porta da imagem abre para o lado do mapa).
- **prompts (pilar 5)**: o plano de takes, os prompts, a revisao_vNN.md e a conferência dos takes gerados.

## Os dois casos do José
**Caso 1, quem sai primeiro.** Nas palavras do José: "o moço abre a porta, conversam e eles saem; no corte para a outra cena, o de azul, que saiu primeiro, está na frente e o de preto atrás."
Regra: a ordem de saída é a ordem de chegada. Quem sai primeiro está na frente no plano seguinte, e a direção de tela continua a mesma (saíram para a esquerda do quadro, seguem para a esquerda). No prompt: o estado final do take N diz a ordem e a direção; o take N+1 começa repetindo as duas.

**Caso 2, a porta.** Nas palavras do José: "O erro mais comum é com porta: o cara entra puxando a porta e, na hora de sair, puxa a porta de novo — não faz sentido. É erro de continuidade; por isso revisar se a física está natural."
(Em termos físicos: puxando de fora na entrada, a porta abriu para fora do cômodo; puxando de dentro na saída, abriu para dentro. Ela trocou de sentido entre um take e outro.)
Regra: a mesma porta abre sempre para o mesmo lado. Quem puxa de fora faz a porta abrir para fora do cômodo; quem puxa de dentro faz a porta abrir para dentro. Puxar na entrada e puxar de novo na saída só acontece se a porta trocou de lado entre um momento e outro: é o erro. Quem entrou puxando sai empurrando. No prompt: dobradiça, lado de abertura e ação com direção em todo take que usa a porta, e a regra repetida nas restrições.

## 1. Mapa da cena
Um por cenário. O pilar visual faz a partir da geografia do universo (pilar roteiro); o pilar prompts copia no plano de takes. Tudo visto da câmera mestre (o plano geral do cenário).

| Elemento | O que registrar | Exemplo |
|---|---|---|
| Porta | parede; lado da dobradiça para quem entra e na tela da câmera mestre; abre para dentro ou para fora do cômodo; de dentro empurra ou puxa; de fora empurra ou puxa; lado da maçaneta; aberta ou fechada no início | fundo; à direita na tela (à esquerda de quem entra pelo corredor); para dentro; de dentro puxa; de fora empurra; maçaneta à esquerda na tela; fechada |
| Janelas | parede; de onde a luz entra | parede esquerda; luz da esquerda |
| Saídas | para onde cada uma leva, e para que lado da tela | porta do fundo → corredor à esquerda do quadro |
| Móveis fixos | posição em relação à câmera mestre | mesa à esquerda, perto da janela |
| Eixo | de que lado da ação a câmera fica | dentro da sala, de frente para o fundo |

| A porta abre... | De fora, para entrar | De dentro, para sair |
|---|---|---|
| para dentro do cômodo | empurra | puxa |
| para fora do cômodo | puxa | empurra |

Porta vai-e-vem, de correr ou giratória é exceção: o mapa diz como funciona. Mapa faltando ou contraditório (o roteiro diz uma coisa, a imagem do cenário mostra outra): não escolha sozinho. PENDENCIAS, ou 1 linha no mural para o colega.

## 2. Direção de tela e regra dos 180°
- Trace o eixo da ação: a linha entre dois personagens que conversam, ou o caminho de quem anda. A câmera fica de um lado só, e o lado vai escrito no plano de takes.
- Quem anda para a esquerda do quadro continua indo para a esquerda no plano seguinte. Saiu pela esquerda, o próximo plano mostra a pessoa entrando pela direita.
- Num diálogo, A à esquerda e B à direita do quadro, até uma ação mudar isso.
- Para cruzar o eixo de propósito: mostre a câmera passando para o outro lado, ou corte para um plano neutro (de frente, de costas, de cima).

## 3. Ordem e posição dos personagens
- Quem entra primeiro, quem sai primeiro, quem fica de cada lado, quem está no primeiro plano e quem está no fundo.
- Posição sempre em relação ao quadro (画面左侧, 画面右侧, 前景, 背景), nunca "à direita dele".
- Diga quantas pessoas há no quadro. 3 ou mais é risco: divida, ou deixe os outros de costas ou fora de foco.

## 4. Olhares
- A olha para a direita do quadro (para B); B olha para a esquerda (para A). Mantenha nos contraplanos.
- Quem olha para algo fora do quadro: diga para que lado; o plano seguinte mostra a coisa do lado coerente.

## 5. Figurino, objetos e estado
- Figurino item por item na bíblia de continuidade, copiado igual em todos os takes. Muda só com ação escrita ("tira o casaco").
- Objeto: em que mão está, onde é largado, onde está no take seguinte. Nada aparece nem some sem ação.
- Estados que continuam: copo cheio, pela metade ou vazio; porta aberta ou fechada; luz acesa ou apagada; roupa molhada, suja ou rasgada; ferimento; cabelo.

## 6. Luz, hora e clima
- Direção da luz fixa por cenário (luz de janela vindo da esquerda do quadro), a mesma em todos os takes daquele cenário.
- Hora e clima só mudam com corte de tempo escrito no roteiro.
- Fonte de luz visível (janela, abajur, tela) coerente com as sombras.

## 7. Física
| Tema | Confira |
|---|---|
| Gravidade | o que cai, cai; nada flutua; líquido escorre para baixo |
| Inércia | quem corre não para de uma vez; a porta empurrada gira até alguém segurar ou ela bater |
| Líquidos | o nível do copo bate com o que foi bebido; só derrama de recipiente inclinado |
| Tecido | casaco, cabelo e cortina reagem ao movimento e ao vento, e o vento sopra de um lado só |
| Mão e objeto | a mão pega antes de o objeto se mexer; o objeto não se move sozinho; cinco dedos |
| Peso e escala | o pesado é carregado com esforço; a porta é mais alta que a pessoa; tamanhos e distâncias iguais de um take para o outro |
| Causa e som | o clique vem quando a maçaneta gira; o passo soa quando o pé toca o chão |
| Uma coisa por vez | uma ação principal por trecho; nada de três gestos no mesmo segundo |

## 8. Pontes entre takes
- O último estado do take N é o primeiro estado do take N+1: posições, ordem, olhar, figurino, objetos, porta, luz, som e direção do movimento.
- Quando o modelo permitir, use o último quadro do take N como primeiro quadro do take N+1 (o _fim.png que o pilar prompts extrai), ou a extensão nativa, com o quadro de fronteira descrito antes da ação nova.
- Em todo take, declare de novo a geografia e a direção de tela: o modelo não guarda a câmera de uma geração para a outra.
- A bíblia de continuidade (personagens e estética) entra palavra por palavra em todo take.

## 9. Erros comuns de vídeo por IA
| Erro | Como aparece | Prevenção no prompt | Se repetir |
|---|---|---|---|
| Porta que troca de lado | puxa na entrada e na saída; gira sem dobradiça; desliza de lado | mapa da porta + ação com direção + regra nas restrições | porta já aberta; corte no meio da ação; entrada fora do quadro |
| Troca de personagem | rostos ou roupas trocados entre dois personagens | papel estreito para cada referência; descrição fixa; 禁止换脸 | um personagem por take nos planos fechados |
| Gente duplicada | a mesma pessoa duas vezes, ou alguém que surge do nada | 画面中只有这两个人；人物不能重复或分裂 | menos gente no quadro |
| Objeto que surge ou some | o copo aparece na mão, a chave some | objeto, mão e estado escritos em cada trecho | mostrar o antes e o depois, sem a manipulação |
| Mãos | dedos a mais, mão que atravessa o objeto | um gesto simples por vez | cortar a manipulação |
| Texto | letras ilegíveis em placas e papéis | 不要字幕；画面中无任何文字 | texto na edição |
| Figurino que deriva | a jaqueta vira outra ao longo do take | bíblia igual + 服装全程不变 | take mais curto |

As falhas de porta, figurino, identidade com 3 ou mais personagens e mãos foram relatadas por reviewers terceiros no Seedance 2.5 e no Kling 3.0 (a confirmar nos takes do José). Erro que se repete vira regra aqui, pelo pilar skills, na retrospectiva.

## 10. Como escrever no prompt
Sempre em relação ao quadro (画面左侧/右侧), nunca em relação ao personagem. A primeira linha vem da recomendação da pesquisa; as outras são redação do pilar no mesmo padrão.

| Regra | 中文 |
|---|---|
| dobradiça à esquerda do quadro; abre para dentro, para longe da câmera; empurra com a mão direita | 门铰链在画面左侧，门向内、远离镜头方向打开，人物用右手推门 |
| a porta só abre para dentro do cômodo | 这扇门只向室内打开 |
| a porta fica aberta, parada | 门保持敞开，不再移动 |
| o de azul na frente, o de preto atrás | 蓝衬衫男人在前，黑夹克男人在后 |
| da direita para a esquerda do quadro | 从画面右侧向画面左侧走 |
| A à esquerda, B à direita | 人物A在画面左侧，人物B在画面右侧 |
| A olha para B, à direita do quadro | 人物A看向画面右侧的人物B |
| copo na mão direita, pela metade | 他右手拿着一个玻璃杯，杯里的水只剩一半 |
| luz da janela à esquerda, fim de tarde | 傍晚，自然光从画面左侧的窗户照进来 |
| a roupa não muda | 服装全程不变 |
| continua do take anterior | 接上一镜 |
| câmera fixa | 镜头固定不动 |
| só estes dois, sem duplicar | 画面中只有这两个人，人物不能重复或分裂 |

## 11. Formato da revisão
Por take e por ponte: ✅ ok · ✅ corrigido (o pilar corrigiu e diz o que mudou) · ⚠️ precisa do José, sempre com a correção exata (o trecho em mandarim e onde ele entra).

```markdown
# Revisão — takes_v01 · <projeto>
Modelo: Seedance 2.5 · Contra: roteiro_v02, cenarios_v01, storyboard_v01, plano-takes_v01

## take-02
✅ Roteiro: os 3 momentos da cena 2, na ordem.
✅ Porta: dobradiça à direita, abre para dentro; o de azul sai puxando — bate com o mapa.
✅ corrigido: as restrições não repetiam a regra da porta; entrou "门只能向室内打开".
⚠️ Figurino: o roteiro diz que o Léo tira a jaqueta na cena 3, mas o take-03 ainda o descreve de jaqueta. Correção: no take-03, em 主体, trocar "黑色皮夹克" por "黑色T恤，皮夹克搭在左臂上". Decisão do José.

## Pontes
✅ take-01 → take-02: fim = início (os dois à mesa, porta fechada, luz da esquerda).

## Resumo
4 takes · 3 pontes · 9 ✅ · 1 ⚠️
```

Itens a conferir em cada take: roteiro (cada momento, na ordem) · geografia e portas · direção de tela · ordem e posição · olhares · figurino e objetos · luz · física · falas e idioma · contagem de pessoas · texto na tela · duração. O pilar visual usa os mesmos itens, por quadro ou por imagem, no parecer dele.

## Fontes
Pesquisa do Orquestrador em 2026-10-04, por trechos de busca:
- O modelo não guarda a câmera entre gerações; direção de tela por escrito: https://hackernoon.com/ai-video-generation-forgets-where-the-camera-was-heres-the-screen-direction-workflow-that-fixes-it (2026, terceiro, confiança média).
- Modelos de vídeo entendem pouco de física: https://arxiv.org/pdf/2501.09038 (jan. 2025, confiança média).
- Falhas relatadas no Seedance 2.5 (porta, figurino, identidade): https://www.kapwing.com/resources/is-seedance-2-5-actually-better-than-2-0-heres-what-i-found/ (ago. a set. 2026, terceiro, confiança baixa).
- Falhas relatadas no Kling 3.0 (mãos, contato, planos): https://magichour.ai/blog/kling-30-review (2026, terceiro, confiança baixa).
- Quadro de fronteira na extensão: https://dev.to/super_lewis/the-seedance-25-prompting-guide-in-english-4hen (ago. 2026, tradução de terceiro do guia oficial).
- Regra dos 180°, eixo e direção de tela: ofício clássico de montagem e continuidade.

Se a ferramenta mudou, peça ao pilar skills a atualização.

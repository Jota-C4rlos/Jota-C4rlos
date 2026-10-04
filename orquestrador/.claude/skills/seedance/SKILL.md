---
name: seedance
description: Regras e limites do Seedance (ByteDance), o modelo de vídeo padrão do pilar prompts - versões 2.5 e 2.0, duração, extensão, resolução, proporção, áudio nativo, tipos de tarefa, referências e tags @, multi-shot, fórmula e sintaxe do prompt, câmera, tempo, restrições, edição e extensão, onde usar no Brasil e falhas conhecidas. Use quando a OS trouxer MÉTODO seedance ou não trouxer modelo.
user-invocable: false
---
# Seedance

Modelo de vídeo padrão do Orquestrador. Esta skill diz o que o modelo aceita e como ele lê o prompt; a estrutura de cada take é do metodo-take. Fonte: pesquisa de 2026-10-04 feita por trechos de busca (as páginas não abriram). O que tem confiança alta é regra; o resto está marcado **a confirmar**, com o jeito de confirmar.

## 1. Versões
- **Seedance 2.5** é o padrão. Apresentado em 23/06/2026 (Volcano Engine FORCE, Pequim) e lançado em 31/07/2026. A ByteDance pulou da 2.0 para a 2.5; a pesquisa não achou "2.5 Fast" nem "2.5 Mini".
- **Família 2.0** (2.0, 2.0 Fast, 2.0 Mini): continua disponível como opção mais barata e mais rápida, com limites menores (tabela abaixo). Use quando o José pedir teste rápido ou economia. Preço: não pesquisado; não chute.

## 2. Ficha técnica
| Item | Seedance 2.5 | Seedance 2.0 |
|---|---|---|
| Duração por geração | 4 a 30 s | 4 a 15 s |
| Referências por geração | até 50: 30 imagens + 10 vídeos + 10 áudios; vídeo e áudio somam até 30 s | 9 imagens + 3 vídeos + 3 áudios; até 15 s |
| Resolução (API) | 480p, 720p e 1080p, 24 fps, MP4 ou MOV | não pesquisado |
| Proporção | 16:9, 4:3, 1:1, 3:4, 9:16, 21:9 e adaptive (API); no Dreamina também Fit e Original | não pesquisado |
| Áudio | nativo, gerado junto com a imagem: fala com lip-sync, efeitos e música. Aceita até só áudio como referência | não pesquisado |
| Extensão | várias rodadas, para frente, para trás e como ponte entre dois clipes; até cerca de 3 min (**a confirmar**) | — |
| Tamanho do prompt | cerca de 10.000 caracteres (**a confirmar**: dado de terceiro; um provedor limita a 4.000) | cerca de 2.000 (**a confirmar**) |

- Os "29 s" do José são, provavelmente, o teto de 30 s arredondado: nenhuma plataforma encontrada limita a 29 s. A duração-alvo de cada take é do José.
- 4K: o Dreamina e o Jimeng anunciam, mas análises independentes dizem que é upscale. Não conte com 4K nativo.
- Na API, o áudio vem ligado por padrão (generate_audio = true). No Dreamina e no CapCut, o José confere se a tela tem a opção de desligar (**a confirmar**).

## 3. Onde o José usa, do Brasil
- **Dreamina** (web, global, sem documento chinês): estreia global do 2.5 em 31/07/2026. **CapCut**: liberado para assinantes com 16 anos ou mais na América do Sul, na Europa, na Ásia, no Oriente Médio e na África nas semanas seguintes. (**a confirmar** na conta do José: se o 2.5 aparece, o 1080p, o modo beta de vídeo longo de 5 a 180 s e o custo em créditos de um clipe de 30 s.)
- Jimeng e Doubao são produtos da China. API: BytePlus ModelArk (anúncio em 06/08/2026) e Volcano Ark (07/08/2026). Também em terceiros: Runway, PixVerse, fal, OpenArt, Higgsfield, Krea.
- O Dreamina e o CapCut aceitam prompt em 11 idiomas, entre eles português e chinês (**a confirmar**).
- **Filtro de rosto** (relato de terceiros, **a confirmar**): o Dreamina pode bloquear referência com rosto humano fotorrealista de pessoa real sem verificação; retratos gerados por IA, ilustrações e 3D costumam passar. Antes do primeiro projeto, o José sobe uma imagem de personagem do Midjourney e vê se passa. Foto de pessoa real só com direito de imagem.

## 4. Tipos de tarefa
O modelo deduz o tipo pelos materiais enviados e pelo prompt.

| Tipo | Materiais | Quando usar no Orquestrador |
|---|---|---|
| Texto → vídeo (文生视频) | só o prompt | plano sem personagem recorrente (abertura, paisagem) |
| Primeiro quadro (首帧) | 1 imagem | começar exatamente num quadro do storyboard ou no último quadro do take anterior |
| Primeiro e último quadro (首尾帧) | 2 imagens | take com começo e fim fixos, como ponte entre dois takes aprovados |
| Referência multimodal (全模态参考) | imagens, vídeos e áudios citados por @ | o padrão: personagens e cenários pelas imagens do P3 |
| Edição | vídeo + palavra de edição | trocar um detalhe com controle por tempo ("local repaint") |
| Extensão | vídeo + palavra de extensão | continuar uma ação além de 30 s |

O protocolo da casa para ajuste é gerar o take de novo, do zero. A edição é uma alternativa que o José pode testar quando o take estiver quase todo certo.

## 5. Referências e tags @
- Cada arquivo é citado pela tag com o número da ordem de upload: @图片1 (ou @image1), @video1, @audio1. Use a forma que a plataforma mostrar ao subir o arquivo.
- Dê a cada referência um papel explícito e estreito: `@图片1 只定义人物A的脸和发型；@图片2 只定义人物A的服装`. Não confie em rótulo escrito dentro da imagem.
- Storyboard à risca: envie os quadros como imagens na ordem e diga na primeira frase que eles são keyframes em ordem. O guia oficial em inglês usa "Use Images X to X in order as keyframes"; em mandarim, `按顺序将@图片1至@图片3作为关键帧` é tradução do pilar (**a confirmar** no primeiro teste).
- No Dreamina, o recurso Multiframes organiza até 10 quadros de referência, com a duração de cada trecho.

## 6. Multi-shot e plano-sequência
- Um prompt pode ter vários planos encadeados; o modelo corta mantendo estilo e personagem.
- O número máximo de planos por prompt não é documentado. Comece com 3 a 6 num take de 30 s.
- Tempo contínuo e realista: não acumule ações num intervalo curto nem troque de câmera a cada segundo.
- Plano-sequência (一镜到底) também funciona: o exemplo oficial é um take de 30 s com gimbal na mão, entrando pelos bastidores até o palco.
- Oclusão como transição (exemplo oficial): o corpo do personagem passa rente à lente e a câmera segue para o outro personagem.

## 7. Fórmula e sintaxe
Fórmula oficial: **主体 + 动作/事件 + 场景与环境 + 视觉风格 + 运镜/切镜 + 声音**. Só sujeito e ação são obrigatórios. Comece com uma frase-resumo (sujeito, lugar, evento, estilo, câmera especial) e escreva como um brief de diretor: materiais, história, o que acontece no tempo e direção.

| Símbolo | Uso |
|---|---|
| ( ) | música: (背景播放舒缓节奏的钢琴乐) |
| < > | efeito sonoro: <远处传来钟声> |
| { } | fala; não aparece escrita na tela: {你好，欢迎回来} |
| 【 】 | texto na tela: 【第一章：启程】 |

- Fala e legenda são canais separados: para a fala aparecer escrita, ela também vai em 【】.
- O chinês é o idioma padrão das falas. Fala em outro idioma: declare antes, `台词语言 + variante ou sotaque + jeito de falar + quem fala + {fala}`. Exemplo oficial: `台词语言：美式英语。女孩用自然、口语化的美式英语说：{I thought you weren't coming.}` Para o José: `台词语言：巴西葡萄牙语。男人用巴西葡萄牙语低声说：{Eu não volto mais pra lá.}` (a regra é oficial; a qualidade da fala e do lip-sync em português fica **a confirmar** no primeiro take com fala).
- Todas as falas de um clipe no mesmo idioma; repita a declaração antes de cada fala. Sem a declaração, o modelo pode falar no idioma ou no sotaque errado. Não misture idiomas no resto do prompt, exceto nomes próprios.
- Fala entre aspas duplas no lugar de {}: provedores terceiros dizem que funciona, o guia oficial usa {}. Use {}.

## 8. Câmera
Termos reconhecidos pelo guia oficial (em inglês). A coluna em chinês é a tradução usual do pilar: confira com os exemplos do José.

| Português | Guia oficial | 中文 |
|---|---|---|
| plano geral · médio · close | wide · medium · close-up | 远景/全景 · 中景 · 特写 |
| aproximar · afastar | push-in · pull-back | 镜头推近 · 镜头拉远 |
| panorâmica · acompanhar · orbitar | pan · tracking · orbit | 摇镜头 · 跟拍 · 环绕运镜 |
| contra-plongée · vista de cima · primeira pessoa | low angle · overhead · FPV | 仰拍 · 俯拍 · 第一人称视角 |
| câmera na mão · aérea · troca de foco | handheld · aerial · rack focus | 手持镜头 · 航拍 · 焦点转移 |
| câmera fixa · plano-sequência | — | 固定机位 · 一镜到底 |

Um movimento principal por plano. Instruções de câmera não podem se contradizer.

## 9. Tempo
Precisão de 1 segundo: intervalo (`0–3秒：`), momento exato (`第5秒`) ou relativo (`三秒后`). O Jimeng afirma erro menor que 1 s.

## 10. Restrições
Não há campo de prompt negativo documentado (**a confirmar** na tela do Dreamina): as restrições essenciais vão em texto, no fim do prompt. Exemplos vistos em guias de terceiros: `不要字幕；无任何文字出现` · `无背景音乐` · `禁止换脸；禁止面部变形` · `画面中只有[X]；禁止出现其他人`.
- Música do pilar 6 na edição: `无背景音乐`, e só ambiente e efeitos com <>.
- Sem legenda gravada: `不要字幕；画面中无任何文字`.

## 11. Editar e estender
- Edição: o prompt precisa de pelo menos uma destas palavras: 编辑视频, 增加/加上, 删除/去掉, 修改/替换/改成.
- Extensão: pelo menos uma destas: 向前延长 / 向后延长, 延续, 续写.
- Extensão para frente: o primeiro quadro novo continua o último do original. Descreva primeiro o quadro de fronteira (pose e olhar, posição dos objetos, fundo e relações espaciais, posição e enquadramento da câmera, luz, som, direção do movimento) e só depois a ação nova. Identidade, roupa, objetos-chave, fundo e eixo da câmera não mudam, e ninguém duplica nem se divide. Extensão para trás: diga quais materiais pertencem só ao original, senão objetos aparecem cedo demais. (Tradução de terceiro do guia oficial: **a confirmar** no original.)
- Cada extensão gera um clipe novo, só com o trecho novo; o original não muda (terceiros). No Orquestrador, a extensão é um take novo, com arquivo próprio.
- Existe uma skill oficial de otimização de prompt, instalável por NPX (`/sd25-pe`). Não instale: só com a aprovação do José, depois de o pilar skills avaliar.

## 12. Configuração por take (o que vai no takes_vNN.md)
Modelo e versão · tipo de tarefa · duração · proporção (a mesma da imagem de referência ou do primeiro quadro) · resolução · áudio ligado ou desligado · arquivos na ordem de upload · prompt inteiro, colado de uma vez · nome do arquivo para salvar.

## 13. Falhas conhecidas
Relatos de reviewers terceiros sobre o 2.5 (confiança baixa; **a confirmar** nos takes do José). A prevenção está na skill continuidade-e-fisica.
- Figurino que deriva ao longo da sequência (uma jaqueta de couro com tachas virou bomber).
- Proporções que mudam.
- Porta empurrada que "girou sem dobradiça e deslizou de lado".
- Identidade que se perde com 3 ou mais personagens.
- Deformação em ação rápida; objetos mecânicos (dobrar, montar, engrenar) deformam mais que no 2.0.
- Texto na tela fraco.
- Um clipe de 30 s pode sair bom no começo e inutilizável no meio: cena de risco vai em take mais curto.
Em geral, modelos de vídeo entendem pouco de física, e o realismo visual não garante a física certa (estudos de 2025, sem o Seedance). E o modelo não guarda a posição da câmera de uma geração para a outra: cada take declara de novo a geografia e a direção de tela.

## 14. A confirmar
| O quê | Como confirmar |
|---|---|
| Extensão até ~3 min e modo de vídeo longo na conta do José | o José abre a tela do Dreamina ou do CapCut e conta o que aparece |
| 1080p e créditos de um clipe de 30 s | idem; registrar em _Sistema/ferramentas-e-contas.md, com data |
| Campo de prompt negativo e opção de desligar o áudio | idem |
| Filtro de rosto com imagens do Midjourney | teste com uma imagem de personagem antes do projeto |
| Limite de caracteres do prompt e de planos por prompt | o pilar skills confere o guia oficial (links abaixo) |
| Regra do quadro de fronteira | o pilar skills lê o guia oficial em chinês |

## Fontes
Pesquisa do Orquestrador em 2026-10-04, por trechos de busca:
- Lançamento e exemplos oficiais: https://seed.bytedance.com/en/blog/one-take-creation-flexible-referencing-introducing-seedance-2-5 (31/07/2026).
- Duração, resolução e proporção: https://docs.byteplus.com/en/docs/ModelArk/2607688 (ago. 2026).
- Multi-shot e keyframes: https://docs.byteplus.com/en/docs/ModelArk/2607689 (ago. 2026).
- Fórmula, sintaxe, falas, tipos de tarefa, edição e extensão: https://docs.volcengine.com/docs/ark/seedance-2-5?lang=zh (ago. 2026).
- Áudio e referências: https://www.volcengine.com/activity/seedance25 (jul. 2026).
- Câmera, tempo e restrições: https://ai.byteplus.com/resources/how-to-write-better-seedance-2-5-prompts (ago. 2026).
- Extensão no Dreamina: https://dreamina.capcut.com/seedance/seedance-2-5 (ago. a set. 2026, confiança média).
- Onde usar e idiomas: https://www.capcut.com/newsroom/giving-creators-more-control-with-dreamina-seedance-2-5-and-dola-seedream-5-0-pro e https://dreamina.capcut.com/resource/seedance-2-5-launch (31/07/2026, confiança média).
- Quadro de fronteira: https://dev.to/super_lewis/the-seedance-25-prompting-guide-in-english-4hen (ago. 2026, terceiro).
- Filtro de rosto: https://www.renderforest.com/blog/how-to-use-seedance-2-5 (ago. 2026, terceiro, confiança baixa).
- Tamanho do prompt: https://www.layer3labs.io/guides/seedance-2-5-limits (31/07/2026, terceiro, confiança baixa).
- Falhas: https://www.kapwing.com/resources/is-seedance-2-5-actually-better-than-2-0-heres-what-i-found/ (ago. a set. 2026, terceiro, confiança baixa).
- Física: https://arxiv.org/pdf/2501.09038 (jan. 2025).
- Câmera entre gerações: https://hackernoon.com/ai-video-generation-forgets-where-the-camera-was-heres-the-screen-direction-workflow-that-fixes-it (2026, terceiro).

Se a ferramenta mudou, peça ao pilar skills a atualização.

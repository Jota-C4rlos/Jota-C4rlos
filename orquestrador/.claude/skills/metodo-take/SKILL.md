---
name: metodo-take
description: Método Take do José para os prompts de vídeo - um prompt em mandarim por take, com tags de referência, entrada de personagens e cenários, áudio, duração, continuidade entre takes e ajustes que mudam só o erro. RASCUNHO - usa uma estrutura provisória até o José mandar a dele e os cerca de 20 exemplos. Use em toda OS do pilar prompts.
user-invocable: false
---
# Método Take (rascunho)

Estado: **rascunho**. As regras da seção 1 são do José e valem desde já. A estrutura do prompt da seção 4 é **provisória — será substituída pela estrutura do José** quando ele mandar o método e os cerca de 20 prompts de exemplo em mandarim. Até lá, ela segue a fórmula oficial do Seedance 2.5.

"Método Take" não existe publicamente: é o método do José. Não procure na internet nem complete com o que for público.

Modelos dos entregáveis (plano de takes, takes, ajustes, Biblioteca, conferência): [modelos.md](modelos.md), nesta pasta.

## 1. O que o José já definiu (vale sempre)
- **Um prompt por take.** Take é uma geração do modelo de vídeo. Extensão também é um take, com prompt próprio.
- **Sempre em mandarim**, com a tradução em português ao lado, para o José revisar. As falas ficam no idioma do vídeo (seção 4).
- **Tags**: antes de escrever, saber todas as tags do projeto. Até a estrutura do José chegar, tags são as referências @ (cada imagem com um papel) e os símbolos de som e texto. Se o método Take tiver tags próprias, elas entram aqui.
- **Onde cada personagem e cada cenário entra**: em que take, por qual lado da tela, com qual imagem de referência.
- **Áudio sim ou não** em cada take: fala, efeitos, música.
- **Duração por take** dentro do teto do modelo. O José falou em "uns 29 segundos": o teto do Seedance 2.5 é 30 s (4 a 30 s por geração). A duração-alvo de cada take é do José.
- **Continuidade**: estender tem de ser contínuo e seguir a lógica da cena e do ambiente. Quem saiu primeiro está na frente no corte seguinte; a porta abre sempre para o mesmo lado.
- **Revisão**: cada take contra o roteiro, a física e cada momento (skill continuidade-e-fisica).
- **Ajuste**: o prompt volta completo, para gerar do zero. Muda só o que deu errado; o que funcionou fica igual (seção 6).
- **Quem gera é o José.** Modelo padrão: Seedance 2.5. Alternativa: Kling (skill kling).

## 2. Perguntas certas
Antes do plano, confira o que o briefing, o status e o roteiro já respondem. Pergunte só o resto, até 4 por rodada.

| Pergunta | Por que muda o prompt | Sugestão padrão |
|---|---|---|
| A fala é gerada no take ou entra na edição? | {} no prompt e lip-sync, ou take sem fala | gerar no take, se houver fala; uma pessoa falando por vez |
| A música vem do pilar 6 (Suno ou ElevenLabs)? | sem música no take, para não brigar com a trilha | sim: 无背景音乐 e só ambiente e efeitos |
| Duração-alvo de cada take? | onde cortar o roteiro | até 30 s; cena de risco em take mais curto |
| Proporção e resolução? | configuração e enquadramento | a do briefing; 1080p |
| Quais imagens de referência estão aprovadas? | as tags @ de cada take | as do parecer visual do P3 |
| Legenda gravada no vídeo? | 【】 ou 不要字幕 | sem legenda; texto na edição |
| Modelo e versão? | teto, sintaxe e falas | Seedance 2.5 |

## 3. Do roteiro ao plano de takes
1. Some a duração do roteiro e divida pelo teto do modelo. Corte nos "Corte:" do roteiro ou no fim de uma ação, nunca no meio de uma porta abrindo (salvo se o corte no meio for a saída escolhida para o risco).
2. Por take: no máximo 2 personagens falando; um movimento de câmera principal por plano; de 3 a 6 planos num take de 30 s (regra inicial, empírica: o limite do Seedance não é documentado).
3. Cena de alto risco (porta, mãos, líquido, 3 ou mais pessoas) em take mais curto: um clipe de 30 s pode sair bom no começo e inutilizável no meio.
4. Ponte entre takes. O estado final do take N é o estado inicial do take N+1. Escolha o tipo:
   - **extensão** (延长, 延续 ou 续写): ação contínua, sem corte. O prompt começa pelo quadro de fronteira.
   - **último quadro como primeiro quadro**: o José sobe o _fim.png do take anterior.
   - **corte com redeclaração**: o take começa com 接上一镜 e repete a geografia, as posições e a bíblia de continuidade.
5. Mapa de tags: cada imagem aprovada ganha um papel fixo (rosto e figurino de quem, ou layout e luz de qual cenário). Em cada take, a ordem de upload define o @图片N: anote "subir nesta ordem".

## 4. Estrutura do prompt (provisória — será substituída pela estrutura do José)
Base: a fórmula oficial do Seedance 2.5, **主体 + 动作/事件 + 场景与环境 + 视觉风格 + 运镜/切镜 + 声音** (sujeito + ação/evento + cena e ambiente + estilo visual + câmera e corte + som). Só sujeito e ação são obrigatórios. O guia oficial em inglês manda abrir com uma frase-resumo e escrever como um brief de diretor.

Blocos, nesta ordem. O cenário vem antes da linha do tempo porque a ação depende da geografia (decisão do pilar; se o José preferir a ordem oficial à risca, troque):
1. **概述** — uma frase: sujeito, lugar, evento, estilo e câmera especial.
2. **参考** — o papel estreito de cada referência: `@图片1 只定义……的脸、发型和服装`.
3. **主体** — cada personagem com a descrição fixa da bíblia, igual em todos os takes.
4. **场景与环境** — o cenário e a geografia: porta (dobradiça, para onde abre), janelas, saídas, luz e hora.
5. **视觉风格** — a âncora da estética, igual em todos os takes.
6. **开场状态** ou **接上一镜** — o estado inicial, igual ao estado final do take anterior.
7. **时间线** — trechos `0–4秒：`, cada um com ação, enquadramento e câmera, e a fala ou o efeito no momento em que acontece.
8. **声音** — ambiente, música e efeitos do take inteiro.
9. **结尾状态** — o estado final: vira o estado inicial do próximo take.
10. **限制** — as restrições, sempre no fim (não há campo de prompt negativo documentado).

Sintaxe oficial do Seedance 2.5:

| Símbolo | Uso | Exemplo |
|---|---|---|
| ( ) | só música | (背景播放舒缓节奏的钢琴乐) |
| < > | só efeito sonoro | <远处传来钟声> |
| { } | só fala; não aparece escrita na tela | {你好，欢迎回来} |
| 【 】 | só texto na tela | 【第一章：启程】 |
| @图片1, @video1, @audio1 | referência pela ordem de upload | @图片1 只定义人物A的脸和发型 |

- Os símbolos ficam reservados. Tempo em texto simples (`0–4秒：`), nunca `【0–4秒】`; nota de câmera nunca entre parênteses. (Inferência da pesquisa, não confirmada no guia oficial: evita que o modelo leia a marca como texto na tela ou música.)
- Tempo com precisão de 1 segundo: intervalo (0–3秒), momento (第5秒) ou relativo (三秒后).
- Fala que não é em chinês: declare o idioma antes da linha e escreva a fala no próprio idioma, dentro de {}. Fórmula oficial: 台词语言 + variante ou sotaque + jeito de falar + quem fala + {fala}. Um idioma falado por take; repita a declaração antes de cada fala.
- Extensão: a palavra-chave (向后延长, 延续 ou 续写) e, primeiro, o quadro de fronteira (pose, olhar, posições, câmera, luz, som, direção do movimento); só depois a ação nova.
- No Kling, os blocos são os mesmos, mas a sintaxe muda (planos, falas, referências): siga a skill kling, seção 10.

## 5. Exemplo completo (provisório)
Cena original: dois homens terminam uma conversa num escritório; o de camisa azul abre a porta e sai primeiro, o de jaqueta preta vai atrás. Take de 12 s, Seedance 2.5, referência multimodal, fala em português, música na edição. O erro de porta é evitado assim: a geografia vem declarada (dobradiça, para onde abre), a ação diz a direção (puxa para si, na direção da câmera), a porta fica aberta (sem fechar, menos risco) e a regra se repete em 限制.

```text
概述：写实电影风格。白天的小办公室里，两个男人结束谈话，穿蓝衬衫的男人先把门拉开走出去，穿黑夹克的男人跟在后面。固定机位，一镜到底。
参考：@图片1 只定义蓝衬衫男人的脸、发型和服装；@图片2 只定义黑夹克男人的脸、发型和服装；@图片3 只定义办公室的布局、门的位置和光线。
主体：蓝衬衫男人，三十岁左右，黑色短发，浅蓝色衬衫，深灰色长裤。黑夹克男人，四十岁左右，寸头，黑色皮夹克，黑色长裤。
场景与环境：现代小办公室，下午。镜头在房间里，正对后墙。后墙中间偏右有一扇深色木门，门铰链在门的右侧，门把手在门的左侧。这扇门只向室内打开，也就是朝镜头方向打开。门外是一条较暗的走廊，走廊向画面左侧延伸。画面左侧的墙上有一扇窗，自然光从画面左侧照进来。
视觉风格：写实电影质感，自然光，柔和的暖色调，景深适中，门和人物都清晰。
开场状态：两人面对面站在画面左侧的办公桌旁，蓝衬衫男人离门更近，黑夹克男人背对窗户。门是关着的。
时间线：
0–4秒：中景，镜头固定。黑夹克男人看着蓝衬衫男人，压低声音。台词语言：巴西葡萄牙语。黑夹克男人用巴西葡萄牙语低声、平静地说：{Vamos. Antes que ele volte.} 蓝衬衫男人点头。
4–8秒：蓝衬衫男人先转身，走到门的左侧，用右手握住门把手，把门朝自己、朝镜头方向拉开。门绕右侧铰链向室内转开，停在门口右边。黑夹克男人跟在他身后。
8–12秒：蓝衬衫男人先跨出门口，进入走廊，向画面左侧走去；黑夹克男人紧跟在他后面走出门口。门保持敞开，不再移动。
声音：安静的办公室环境音。<门把手转动的咔哒声> <门轴轻微的吱呀声> <两人走远的脚步声>
结尾状态：办公室里没有人。门向室内敞开，停在门口右边。透过门口能看到走廊里的两人：蓝衬衫男人在前，黑夹克男人在后，都朝画面左侧走。
限制：无背景音乐；不要字幕，画面中无任何文字；门只能向室内打开，不能推向走廊；门铰链始终在门的右侧；画面中只有这两个男人，人物不能重复或分裂；禁止换脸；两人的服装全程不变；镜头不移动。
```

Tradução:
> **Resumo**: estilo de cinema realista. Num escritório pequeno, de dia, dois homens terminam a conversa; o de camisa azul abre a porta puxando e sai primeiro, o de jaqueta preta vai atrás. Câmera fixa, plano-sequência.
> **Referências**: @图片1 define só o rosto, o cabelo e a roupa do homem de camisa azul; @图片2, só os do homem de jaqueta preta; @图片3, só o layout do escritório, a posição da porta e a luz.
> **Sujeitos**: camisa azul, uns 30 anos, cabelo preto curto, camisa azul-clara, calça cinza-escura. Jaqueta preta, uns 40 anos, cabelo raspado, jaqueta de couro preta, calça preta.
> **Cenário**: escritório moderno pequeno, à tarde. A câmera está dentro da sala, de frente para a parede do fundo. Nela, um pouco à direita do centro, há uma porta de madeira escura: dobradiça no lado direito da porta, maçaneta no esquerdo. Essa porta só abre para dentro da sala, isto é, na direção da câmera. Do lado de fora, um corredor mais escuro segue para a esquerda do quadro. Há uma janela na parede da esquerda; a luz natural entra pela esquerda.
> **Estilo**: textura de cinema realista, luz natural, tons quentes e suaves, profundidade de campo média: porta e personagens nítidos.
> **Estado inicial**: os dois frente a frente junto à mesa, no lado esquerdo do quadro; o de camisa azul mais perto da porta; o de jaqueta preta de costas para a janela. A porta está fechada.
> **0–4 s**: plano médio, câmera fixa. O de jaqueta preta olha para o de camisa azul e baixa a voz. Idioma da fala: português do Brasil. Ele diz, baixo e calmo, em português: {Vamos. Antes que ele volte.} O de camisa azul faz que sim.
> **4–8 s**: o de camisa azul se vira primeiro, vai até o lado esquerdo da porta, pega a maçaneta com a mão direita e puxa a porta para si, na direção da câmera. A porta gira na dobradiça da direita, para dentro da sala, e para à direita do vão. O de jaqueta preta vem atrás dele.
> **8–12 s**: o de camisa azul passa primeiro pela porta, entra no corredor e segue para a esquerda do quadro; o de jaqueta preta sai logo atrás. A porta fica aberta, parada.
> **Som**: ambiente de escritório silencioso. <clique da maçaneta girando> <rangido leve da dobradiça> <passos dos dois se afastando>
> **Estado final**: o escritório vazio. A porta aberta para dentro, parada à direita do vão. Pelo vão se veem os dois no corredor: camisa azul na frente, jaqueta preta atrás, os dois indo para a esquerda do quadro.
> **Restrições**: sem música de fundo; sem legenda, nenhum texto na imagem; a porta só abre para dentro da sala, nunca empurrada para o corredor; dobradiça sempre no lado direito; só estes dois homens, sem duplicar nem dividir pessoas; proibido trocar rostos; a roupa dos dois não muda; a câmera não se mexe.

Ponte para o take seguinte (começo do prompt dele):
```text
接上一镜：走廊，侧面跟拍。蓝衬衫男人在前，黑夹克男人在后，两人从画面右侧向画面左侧走。
```
> Continuação do take anterior: corredor, travelling lateral. Camisa azul na frente, jaqueta preta atrás, os dois andando da direita para a esquerda do quadro.

## 6. Ajustes
1. Leia o relato do José e ache o trecho exato do prompt que causou o erro.
2. Mude só esse trecho e, se precisar, a restrição ligada a ele. O resto fica igual, palavra por palavra.
3. Devolva o prompt completo, numa nova versão do takes, com o "antes → depois" curto. Exemplo, relato "na saída a porta abriu para o corredor":
   - antes: `用右手握住门把手，把门朝自己、朝镜头方向拉开。`
   - depois: `用右手握住门把手，向后退一步，把门朝自己、朝镜头方向拉开，门板向室内转开。`
   - e em 限制: `门不能向走廊方向打开` entra ao lado de `门只能向室内打开`.
4. Se o ajuste mudar o estado final, avise sobre a ponte com o take seguinte; não mude o outro take por conta própria.
5. Mesmo erro 2 vezes depois de ajustado: proponha outra saída (porta já aberta, corte no meio da ação, take mais curto, primeiro e último quadro).

## 7. Por que mandarim
É escolha do José, e vale. A pesquisa (2026-10-04) não achou declaração oficial de que prompt em chinês rende mais no Seedance, e os relatos da comunidade se contradizem: uns dizem que o inglês dá câmera e estilo mais estáveis; outros, que o filtro de conteúdo é mais rígido com inglês. O oficial: o chinês é o idioma padrão das falas, o Dreamina aceita 11 idiomas (português e chinês entre eles) e não se deve misturar idiomas no prompt, exceto a fala declarada e nomes próprios. Se o José quiser tirar a dúvida, o pilar skills faz um teste A/B: o mesmo take em mandarim e em inglês, com a mesma imagem inicial.

## 8. Como esta skill se forma (pilar skills)
- O José põe a estrutura do Take e os cerca de 20 exemplos em _Sistema/academia/material/metodo-take/ (veja o LEIA-ME de lá) e pede "abra o curso do método Take".
- O pilar skills lê o material e reescreve esta skill: a estrutura do José no lugar da seção 4, as tags dele, as regras tiradas dos exemplos (o que funcionou e o que deu errado) e de 2 a 3 exemplos curtos. Os exemplos inteiros ficam na pasta de material, fora do git. A versão final traz um índice de todos os exemplos (nº, cena, o que ensina, arquivo em _Sistema/academia/material/metodo-take/), sem copiar o conteúdo: o pilar prompts lê os 1 ou 2 mais parecidos com a cena antes de escrever.
- Com o "aprovado" do José, o catálogo marca a skill como ativa.
- Takes que funcionaram de primeira (Biblioteca/prompts/) e erros que se repetem em _Sistema/licoes/registro.md alimentam as próximas versões.

## Fontes
Pesquisa do Orquestrador em 2026-10-04, por trechos de busca (as páginas não abriram):
- Fórmula, sintaxe de som e texto, regra das falas, palavras de edição e extensão: https://docs.volcengine.com/docs/ark/seedance-2-5?lang=zh (ago. 2026).
- 4 a 30 s por geração: https://docs.byteplus.com/en/docs/ModelArk/2607688 (ago. 2026).
- Referências @ e limites: https://www.volcengine.com/activity/seedance25 (jul. 2026).
- Câmera e tempo: https://ai.byteplus.com/resources/how-to-write-better-seedance-2-5-prompts (ago. 2026).
- Quadro de fronteira na extensão: https://dev.to/super_lewis/the-seedance-25-prompting-guide-in-english-4hen (ago. 2026, tradução de terceiro do guia oficial; a confirmar no original).
- Chinês x inglês, sem declaração oficial: https://x.com/mitte_ai/status/2026254164481716476 (fev. 2026, terceiro, confiança baixa).
- Nenhum método público chamado "método Take" foi encontrado (busca de 2026-10-04).

Se a ferramenta mudou, peça ao pilar skills a atualização.

# Modelos de prompt — Midjourney V8.2

Troque o que está entre <>. Os pedaços em colchetes vêm das fichas, copiados palavra por palavra:
- [MEIO] e [ÂNCORA DE ESTILO]: da estética do projeto (estetica_vNN.md). No hiper-realista, [MEIO] fica vazio e o prompt abre pelo sujeito; a lente vai junto do enquadramento (muda com o plano), e a câmera, o filme e o grão ficam na âncora.
- [PARÂMETROS]: os da série (ex.: `--raw --s 100`). O `--ar` vem indicado em cada modelo.
- [BLOCO <NOME>]: o bloco-âncora completo do personagem ou do cenário.
- [TAG <NOME>]: a versão curta do personagem (8 a 15 palavras: os traços que o identificam e o figurino da cena). Vai nos quadros que têm o retrato anexado, para o prompt não ficar comprido. Também é literal.
- [LUZ <CENÁRIO>]: a regra de luz da ficha do cenário.

Todo prompt vai na ficha com a tradução em português embaixo e o nome do arquivo.

## Personagem

### 1. Retrato de referência
```
[MEIO] portrait of [BLOCO PERSONAGEM], <expressão neutra da ficha>, head and shoulders, slight three-quarter angle, even soft neutral light, plain light grey background, [ÂNCORA DE ESTILO] [PARÂMETROS] --ar 3:4
```
Salvar como: personagem-<nome>-retrato_NN.png

### 2. Corpo inteiro
Anexar no Edit Model: o retrato aprovado.
```
[MEIO] full body shot of [BLOCO PERSONAGEM], standing in a relaxed neutral pose, arms at the sides, feet visible, plain light grey background, even soft light, [ÂNCORA DE ESTILO] [PARÂMETROS] --ar 9:16
```
Salvar como: personagem-<nome>-corpo_NN.png

### 3. Turnaround (heurística de comunidade, sem doc oficial)
Anexar: o retrato e o corpo inteiro aprovados.
```
character turnaround sheet of [BLOCO PERSONAGEM], front view, three-quarter view, side profile, back view, full body, neutral standing pose, plain white background, same outfit in every view, even soft lighting, [ÂNCORA DE ESTILO] [PARÂMETROS] --ar 16:9 --no text, labels
```
Salvar como: personagem-<nome>-turnaround_NN.png

### 4. Expressões (heurística)
Anexar: o retrato aprovado.
```
expression sheet of [BLOCO PERSONAGEM], six facial expressions of the same character in a three by two grid: <expressão 1>, <expressão 2>, <expressão 3>, <expressão 4>, <expressão 5>, <expressão 6>, head and shoulders, plain light grey background, even soft light, [ÂNCORA DE ESTILO] [PARÂMETROS] --ar 3:2 --no text, labels
```
As expressões saem da ficha, em palavras concretas: "a crooked half smile with eyes looking away", e não "ironic".
Salvar como: personagem-<nome>-expressoes_NN.png

## Cenário

### 5. Plano mestre
```
[MEIO] wide shot of [BLOCO CENÁRIO], seen from <ponto de vista da câmera padrão>, <cada porta: posição, dobradiça na tela, entreaberta, abrindo para dentro ou para fora>, an empty room, [LUZ CENÁRIO], [ÂNCORA DE ESTILO] [PARÂMETROS] --ar <proporção do vídeo>
```
Sugestão: mostre a porta entreaberta no mestre. A imagem fica com o lado da dobradiça e o sentido de abertura visíveis e vira prova para o pilar prompts. Apareceu gente? Acrescente `--no people`.
Salvar como: cenario-<nome>-mestre_NN.png

### 6. Contraplano
Anexar: o mestre aprovado.
```
[MEIO] reverse angle of the same <cômodo> from the reference, seen from <o lado oposto, olhando para ...>, same furniture, materials and light source, [BLOCO CENÁRIO], [LUZ CENÁRIO], [ÂNCORA DE ESTILO] [PARÂMETROS] --ar <proporção do vídeo>
```
No contraplano a luz vem do mesmo lugar físico, então troca de lado na tela: a janela à esquerda no mestre fica à direita no contraplano. Escreva o lado da tela certo no prompt.
Salvar como: cenario-<nome>-contraplano_NN.png

### 7. Detalhe
Anexar: o mestre aprovado.
```
[MEIO] close-up detail of <a porta, o objeto-chave> in the same <cômodo> from the reference, <estado>, [LUZ CENÁRIO], [ÂNCORA DE ESTILO] [PARÂMETROS] --ar <proporção do vídeo>
```
Salvar como: cenario-<nome>-detalhe-<coisa>_NN.png

## Quadro do storyboard

### 8. Quadro
Anexar no Edit Model (até 4): o cenário aprovado do ângulo certo, o retrato de cada personagem que aparece de frente e o corpo inteiro de quem tem figurino importante na cena.
```
[MEIO] <enquadramento e ângulo> inside the <cômodo> from the reference, <de onde a câmera olha>. [TAG A] <ação no instante>, <posição na tela: on the left of frame, in the foreground>, <para onde olha>. [TAG B] <ação>, <posição>. <estado da porta e dos objetos, com a mão certa>. [LUZ CENÁRIO], [ÂNCORA DE ESTILO] [PARÂMETROS] --ar <proporção do vídeo>
```
Sem referência anexada, troque cada [TAG] pelo [BLOCO] completo.
Salvar como: quadro-<NN>_NN.png

## Exemplo completo: "Visita" (hiper-realista, 9:16)
Do roteiro de exemplo da skill roteiro-padrao. Universo: a porta da frente da sala abre para dentro, dobradiça à direita de quem entra; o corredor para os fundos fica à esquerda de quem entra. Com a câmera dentro da sala, olhando para a porta, isso vira: dobradiça à esquerda da tela, corredor à direita da tela.

Estética do projeto:
- [ÂNCORA DE ESTILO]: `natural skin texture, shot on a full-frame cinema camera, Kodak Portra 400, subtle film grain`
- [PARÂMETROS]: `--raw --s 100`

Rui:
- [BLOCO RUI]: `a lean man in his mid-30s with a long oval face, short black hair with a cowlick at the crown, two-day stubble, a thin scar through his left eyebrow, olive skin, wearing a faded navy work jacket over a grey t-shirt, dark jeans and worn brown leather boots`
- [TAG RUI]: `the lean younger man with the scar through his left eyebrow, in a faded navy work jacket`

Antônio:
- [BLOCO ANTONIO]: `a stocky man in his late 60s with a broad square face, deep forehead lines, a thick grey moustache, short white hair, tanned weathered skin, wearing a faded checked flannel shirt with rolled sleeves, brown work trousers and worn leather slippers`
- [TAG ANTONIO]: `the stocky older man with a thick grey moustache, in a faded checked flannel shirt`

Sala:
- [BLOCO SALA]: `a small modest living room of an old single-story house in a countryside town, worn terracotta tile floor, pale green painted walls, a round wooden wall clock, an old floral sofa, a moss green wooden front door with a round brass knob`
- [LUZ SALA]: `soft late morning daylight coming in through the front door, the room dim and warm`

Retrato do Rui (salvar como personagem-rui-retrato_01.png):
```
Portrait of a lean man in his mid-30s with a long oval face, short black hair with a cowlick at the crown, two-day stubble, a thin scar through his left eyebrow, olive skin, wearing a faded navy work jacket over a grey t-shirt, dark jeans and worn brown leather boots, guarded neutral expression, head and shoulders, slight three-quarter angle, 50mm lens at f/2, even soft neutral light, plain light grey background, natural skin texture, shot on a full-frame cinema camera, Kodak Portra 400, subtle film grain --raw --s 100 --ar 3:4
```
Tradução: retrato de um homem magro de uns 35 anos, rosto oval e comprido, cabelo preto curto com redemoinho no alto da cabeça, barba de dois dias, uma cicatriz fina na sobrancelha esquerda, pele morena, jaqueta de trabalho azul-marinho desbotada sobre camiseta cinza, jeans escuro e botas de couro marrom gastas; expressão neutra e na defensiva; cabeça e ombros, leve 3/4, lente 50 mm em f/2; luz suave e neutra; fundo cinza-claro liso; textura natural de pele; câmera de cinema full-frame; filme Kodak Portra 400, grão sutil.

Plano mestre da sala (salvar como cenario-sala-mestre_01.png):
```
Wide shot of a small modest living room of an old single-story house in a countryside town, worn terracotta tile floor, pale green painted walls, a round wooden wall clock, an old floral sofa, a moss green wooden front door with a round brass knob, seen from inside the room looking toward the front door, 28mm lens at f/4, the door slightly ajar and opening inward with its hinge on the left of frame, a narrow corridor opening on the right of frame, an empty room, soft late morning daylight coming in through the front door, the room dim and warm, natural skin texture, shot on a full-frame cinema camera, Kodak Portra 400, subtle film grain --raw --s 100 --ar 9:16
```
Tradução: plano geral de uma sala pequena e simples de uma casa térrea antiga no interior, piso de lajota de barro gasto, paredes verde-claras, relógio redondo de madeira na parede, sofá florido antigo, porta da frente de madeira verde-musgo com maçaneta redonda de latão; visto de dentro da sala, olhando para a porta, lente 28 mm em f/4; a porta entreaberta, abrindo para dentro, com a dobradiça à esquerda da tela; a entrada de um corredor estreito à direita da tela; sala vazia; luz suave do fim da manhã entrando pela porta, a sala na penumbra e quente; mesma âncora de estilo (a lente muda porque o plano é geral; a âncora não muda).

Quadro 02, cena 2 (anexar: cenario-sala-mestre, personagem-antonio-retrato, personagem-rui-retrato, personagem-rui-corpo; salvar como quadro-02_01.png):
```
Medium wide shot inside the living room from the reference, looking toward the open front door, 35mm lens at f/2.8, the moss green door swung inward with its hinge on the left of frame. The stocky older man with a thick grey moustache, in a faded checked flannel shirt stands inside on the left of frame, one hand still on the edge of the open door, looking at the doorway. In the doorway at the center right of frame, the lean younger man with the scar through his left eyebrow, in a faded navy work jacket holds a rusty wrench out at arm's length in his right hand without crossing the threshold, a head taller than the older man. Bright daylight outside behind him, the room dim and warm, natural skin texture, shot on a full-frame cinema camera, Kodak Portra 400, subtle film grain --raw --s 100 --ar 9:16
```
Tradução: plano médio aberto dentro da sala da referência, olhando para a porta da frente aberta, lente 35 mm em f/2.8; a porta verde-musgo aberta para dentro, dobradiça à esquerda da tela. O homem mais velho e atarracado, de bigode grosso grisalho e camisa xadrez de flanela desbotada, está do lado de dentro, à esquerda da tela, ainda com a mão na borda da porta, olhando para a entrada. Na soleira, no centro-direita da tela, o homem mais novo e magro, com a cicatriz na sobrancelha esquerda e a jaqueta azul-marinho desbotada, estende uma chave inglesa enferrujada com o braço esticado, na mão direita, sem cruzar a soleira; ele é uma cabeça mais alto que o mais velho. Luz forte do dia lá fora, atrás dele; a sala na penumbra e quente; mesma âncora de estilo.

Por que está certo: a porta abre para o lado escrito no universo, a dobradiça está do lado certo da tela para esta câmera, a chave está na mão direita (como no roteiro) e a diferença de altura aparece porque os dois estão no quadro.

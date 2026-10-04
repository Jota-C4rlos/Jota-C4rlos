# Catálogo de estéticas — fichas

Tudo aqui é heurística de prática, não verificada em fonte (pesquisa de 2026-10-04): palavras do prompt, parâmetros e sobrevivência imagem → vídeo. Ponto de partida para testar; o que os testes do José confirmarem ou derrubarem entra na próxima atualização. As regras de sintaxe e as faixas de parâmetros estão na skill midjourney.

Em todas: `--exp 0` nas séries (testar 5 ou 10 só na fase de descoberta do look), `--c 0`, o mesmo `--s` em toda a série e `--ar` explícito. `--no` só para artefato que já apareceu, salvo onde a ficha diz que ele é esperado. Os exemplos usam `--ar 9:16`; troque pela proporção do projeto. O descritor em mandarim é uma sugestão ao pilar prompts, que decide a redação final no prompt de vídeo.

## 1. Hiper-realista / cinematográfico (photorealistic, cinematic)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: drama, suspense, histórias do cotidiano, anúncio de produto real, documental; quando o público precisa acreditar que aconteceu. Evitar: criatura fantástica em close (estranheza), qualquer semelhança com pessoa real.
- Palavras do prompt (EN): abre pelo sujeito, na ordem sujeito > ambiente > luz > câmera e lente > estilo e textura. Imperfeições: `natural skin texture, visible pores, stray hairs, fine lines`. Luz com fonte e direção: `soft window light from camera left`, `warm practical tungsten lamp`. Câmera e filme: `shot on a full-frame cinema camera, 50mm lens at f/2, Kodak Portra 400, subtle film grain`. Nunca `hyper-realistic, 4k, masterpiece`. Para mais detalhe de câmeras, lentes e filmes, a skill da conta anthropic-skills:midjourney, se disponível.
- Parâmetros V8.2 (ponto de partida): `--raw --s 50-150` (escolha um valor e repita), 40 a 90 palavras.
- Paleta e luz: luz motivada (janela, lâmpada, poste); a cor descrita como tratamento de cor (`muted teal and amber color grade`).
- Consistência: atributos repetíveis no bloco-âncora; retrato de frente ou 3/4 com luz neutra como referência; a mesma câmera, o mesmo filme e o mesmo grão em toda a série.
- Imagem → vídeo: sobrevivência alta. Riscos: o rosto muda em giros de cabeça e perfis; mãos e dentes; estranheza em close. A confirmar: o Dreamina pode bloquear referência com rosto fotorrealista de pessoa real; retratos gerados por IA costumam passar (relato de terceiros). Como reduzir: takes curtos com uma ação; turnaround para perfis e costas; close só quando a cena pede.
- Descritor para o vídeo (sugestão): 电影感写实风格 (estilo realista com cara de cinema).
- Exemplo:
  `A man in his mid-30s with a thin scar through his left eyebrow and two-day stubble stands at a weathered green front door, gripping a rusty wrench in his right hand, small-town street behind him in late afternoon, warm low sun from camera right, 50mm lens at f/2, natural skin texture, visible pores, shot on a full-frame cinema camera, Kodak Portra 400, subtle film grain --raw --s 100 --ar 9:16`
  Tradução: homem de uns 35 anos, cicatriz fina na sobrancelha esquerda e barba de dois dias, em pé diante de uma porta verde gasta, apertando uma chave inglesa enferrujada na mão direita; rua de cidade pequena atrás, fim de tarde; sol baixo e quente vindo da direita da câmera; lente 50 mm em f/2; textura natural de pele, poros visíveis; câmera de cinema full-frame; filme Kodak Portra 400, grão sutil.

## 2. 3D de animação (stylized 3D animation)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: fábula, humor, público família, animais e objetos que falam, mascote de marca, personagens de expressão exagerada. Evitar: tema que pede peso documental.
- Palavras do prompt (EN): abertura `stylized 3D animated feature film still of` · âncora `rounded appealing shapes, large expressive eyes, soft subsurface scattering skin, global illumination, soft rim light, saturated but harmonious palette`. Nunca nome de estúdio: descreva as características.
- Parâmetros V8.2 (ponto de partida): sem `--raw`; `--s 100-250`. Armadilha: `--raw` com `--s` baixo puxa o material para o realista.
- Paleta e luz: cores saturadas e harmônicas, luz suave, luz de recorte (rim light) separando o personagem do fundo.
- Consistência: as proporções e o tamanho dos olhos variam entre imagens. Escreva na ficha a proporção (cabeça e corpo, olhos) e confira no parecer; turnaround obrigatório para o protagonista.
- Imagem → vídeo: sobrevivência alta (os modelos viram muito 3D animado). Riscos: o rosto "derrete" em movimento rápido; cabeça e olhos mudam de escala. Como reduzir: ações de velocidade moderada; descritor de estilo repetido no prompt de vídeo.
- Descritor para o vídeo (sugestão): 三维动画电影风格 (estilo de filme de animação 3D).
- Exemplo:
  `Stylized 3D animated feature film still of a small round elderly baker with a flour-dusted apron and oversized round glasses, kneading dough on a wooden counter in a cozy bakery at dawn, warm light from a window on the left, rounded appealing shapes, large expressive eyes, soft subsurface scattering skin, global illumination, soft rim light, saturated but harmonious palette --s 175 --ar 9:16`
  Tradução: quadro de filme de animação 3D estilizado: um padeiro idoso, baixinho e redondo, avental sujo de farinha e óculos redondos grandes, sovando massa num balcão de madeira numa padaria aconchegante ao amanhecer; luz quente de uma janela à esquerda; formas arredondadas e simpáticas, olhos grandes e expressivos, pele com translucidez suave, iluminação global, luz de recorte suave, paleta saturada e harmônica.

## 3. 2D cartoon, flat / vetor (flat vector cartoon)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: explicativo, humor simples, conteúdo de marca, ritmo rápido, personagens simbólicos.
- Palavras do prompt (EN): abertura `flat vector cartoon illustration of` · âncora `bold uniform outlines, simple geometric shapes, flat solid colors, limited palette of <cores>, plain background`. Não escreva "no gradients" no texto: use o `--no`.
- Parâmetros V8.2 (ponto de partida): `--s 50-150`; testar com e sem `--raw`. Se aparecerem degradê, volume ou sombra: `--no gradient, 3D render, shading`.
- Paleta e luz: 4 a 6 cores chapadas; quase sem luz (sombra chapada ou nenhuma); fundo simples.
- Consistência: o personagem é feito de formas fáceis de repetir (rosto redondo, olhos de ponto, boné grande). Escreva as formas na ficha; a espessura do contorno é a mesma em tudo.
- Imagem → vídeo: sobrevivência baixa. Riscos: o modelo acrescenta volume e luz, os contornos "respiram", as formas se deformam. Como reduzir: câmera parada, movimentos pequenos, takes curtos.
- Descritor para o vídeo (sugestão): 扁平矢量卡通风格，粗轮廓线，纯色平涂 (cartoon vetorial chapado, contorno grosso, cor lisa).
- Exemplo:
  `Flat vector cartoon illustration of a tall thin delivery guy with a round head, dot eyes and a big orange cap, running with a stack of pizza boxes down a simple city street, bold uniform outlines, simple geometric shapes, flat solid colors, limited palette of orange, teal and cream, plain sky --s 75 --ar 9:16`
  Tradução: ilustração cartoon vetorial chapada: entregador alto e magro, cabeça redonda, olhos de ponto e um boné laranja grande, correndo com uma pilha de caixas de pizza por uma rua simples; contorno grosso e uniforme, formas geométricas simples, cores lisas, paleta de laranja, verde-azulado e creme, céu liso.

## 4. Anime, 2D cel (2D cel-shaded anime)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: ação, emoção intensa, fantasia, romance, público jovem. Nunca nome de estúdio ou diretor.
- Palavras do prompt (EN): abertura `2D cel-shaded anime still of` (ou `anime key visual of`) · âncora `clean lineart, flat cel colors, hard-edged shadows, <luz dramática>, palette of <cores>`.
- Parâmetros V8.2 (ponto de partida): sem `--raw`; `--s 100-250`. Armadilhas: `--raw` ou `--s` baixo dão um "semi-real"; excesso de detalhe tira a cara de animação: simplifique.
- Niji 7: é uma linha separada, fora do V8. Nunca escreva `--niji` num prompt V8. Se o José quiser testar o Niji, o projeto inteiro fica nele, e não está confirmado se o Edit Model funciona lá.
- Paleta e luz: cores chapadas, sombras de borda dura, luz dramática (contraluz, pôr do sol, céu forte).
- Consistência: penteado e cor do cabelo são a assinatura do personagem (silhueta reconhecível); formato e cor dos olhos na ficha; a mesma espessura de linha.
- Imagem → vídeo: sobrevivência média. Riscos: o modelo "tridimensionaliza" (vira 2.5D); as linhas tremem; o rosto muda no meio do movimento; o movimento sai fluido demais para a cara de animação limitada. Como reduzir: câmera estável, ação simples.
- Descritor para o vídeo (sugestão): 二维手绘动画、赛璐璐风格 (animação 2D desenhada à mão, estilo celuloide).
- Exemplo:
  `2D cel-shaded anime still of a teenage girl with a short silver bob and a long red scarf standing on a rooftop at sunset, wind lifting her scarf, city skyline behind her, clean lineart, flat cel colors, hard-edged shadows, warm orange backlight, palette of teal, coral and cream --s 150 --ar 9:16`
  Tradução: quadro de anime 2D: adolescente de cabelo prateado curto (chanel) e cachecol vermelho longo, em pé num terraço ao pôr do sol, o vento levantando o cachecol, a cidade atrás; linha limpa, cores chapadas, sombras de borda dura, contraluz laranja quente, paleta verde-azulado, coral e creme.

## 5. Pixel art (16-bit pixel art)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: games, nostalgia, humor retrô, quando a estética é a própria mensagem. Antes de escolher, o José precisa saber que é a estética que pior sobrevive ao vídeo.
- Palavras do prompt (EN): abertura `16-bit pixel art scene of` · âncora `sprite-style characters, crisp visible pixel grid, limited color palette of <cores>, dithering`.
- Parâmetros V8.2 (ponto de partida): `--s 50-150`; testar com e sem `--raw`. Se aparecer borrado ou suavizado: `--no blur, anti-aliasing`.
- Paleta e luz: paleta curta (descreva as cores), luz chapada, degradê feito com pontilhado (dithering).
- Consistência: pixels de tamanhos misturados e "falso pixel" com bordas suavizadas são comuns. Pode precisar de redução com vizinho mais próximo (nearest-neighbor) ou de um filtro de pixelização na edição.
- Imagem → vídeo: sobrevivência muito baixa. A interpolação borra os pixels, quebra a grade e cria movimento menor que um pixel. Como reduzir: planejar um filtro de pixelização ou de redução de paleta no vídeo final, ou aceitar um visual "inspirado em pixel".
- Descritor para o vídeo (sugestão): 16位像素艺术风格 (estilo pixel art de 16 bits).
- Exemplo:
  `16-bit pixel art scene of a small knight with a blue cape standing at the gate of a ruined castle at night, full moon behind the towers, sprite-style characters, crisp visible pixel grid, limited color palette of deep blues and warm torch orange, dithering --s 100 --ar 9:16`
  Tradução: cena em pixel art de 16 bits: um cavaleiro pequeno de capa azul no portão de um castelo em ruínas, à noite, lua cheia atrás das torres; personagens em estilo sprite, grade de pixels nítida e visível, paleta curta de azuis profundos e laranja de tocha, pontilhado.

## 6. Claymation / stop-motion (claymation)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: humor artesanal, infantil, nostalgia, histórias "feitas à mão", anúncio simpático. Nunca nome de estúdio.
- Palavras do prompt (EN): abertura `claymation stop-motion animation still of` · âncora `plasticine figures with visible fingerprints and tool marks, handmade miniature set, felt and cardboard textures, macro photography, shallow depth of field`.
- Parâmetros V8.2 (ponto de partida): `--raw --s 50-150`, com linguagem de fotografia de miniatura.
- Paleta e luz: cores de massinha saturadas; luz suave de estúdio pequeno; materiais à vista (feltro, papelão, madeira).
- Consistência: as digitais e a textura derivam de imagem para imagem; a proporção de boneco (cabeça grande, mãos simples) fica escrita na ficha.
- Imagem → vídeo: sobrevivência alta no material. Riscos: o movimento sai suave demais e perde a cadência "aos pulos" do stop-motion; as digitais e a textura derivam (risco médio). Como reduzir: pedir no vídeo "stop-motion, choppy 12fps feel"; se preciso, reduzir a taxa de quadros na edição.
- Descritor para o vídeo (sugestão): 定格动画、黏土质感 (animação stop-motion, textura de massinha).
- Exemplo:
  `Claymation stop-motion animation still of a grumpy old fisherman with a yellow raincoat and a bushy white beard, sitting in a tiny wooden boat on a sea of blue felt, cardboard clouds above, plasticine figures with visible fingerprints and tool marks, handmade miniature set, felt and cardboard textures, macro photography, shallow depth of field --raw --s 100 --ar 9:16`
  Tradução: quadro de animação em massinha: pescador velho e ranzinza, capa de chuva amarela e barba branca cheia, sentado num barquinho de madeira num mar de feltro azul, nuvens de papelão; bonecos de massinha com digitais e marcas de ferramenta, cenário em miniatura feito à mão, texturas de feltro e papelão, fotografia macro, pouca profundidade de campo.

## 7. Low-poly (low-poly 3D)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: tecnologia, jogo, explicação, diorama, ritmo calmo.
- Palavras do prompt (EN): abertura `low-poly 3D isometric diorama of` · âncora `flat-shaded faceted polygons, minimal geometry, clean solid colors, <luz direcional>`.
- Parâmetros V8.2 (ponto de partida): `--s 100`. Armadilha: o Midjourney suaviza as facetas. Reforce "faceted, flat-shaded" no texto; se a suavização continuar, `--no smooth shading`.
- Paleta e luz: cores sólidas, uma cor por faceta; luz direcional simples (sol) que marca as facetas.
- Consistência: o nível de detalhe (poucas ou muitas facetas) fica escrito na âncora e não muda.
- Imagem → vídeo: sobrevivência média. Riscos: os polígonos se suavizam ou se "refazem" durante o movimento. Como reduzir: câmera orbitando devagar; descritor repetido no prompt de vídeo.
- Descritor para o vídeo (sugestão): 低多边形 (low-poly).
- Exemplo:
  `Low-poly 3D isometric diorama of a tiny lighthouse on a rocky island at dusk, a small keeper in a red coat climbing the outside stairs, flat-shaded faceted polygons, minimal geometry, clean solid colors, soft orange sun from the left --s 100 --ar 9:16`
  Tradução: diorama isométrico low-poly de um farol pequeno numa ilha de pedra ao entardecer, um faroleiro de casaco vermelho subindo a escada de fora; polígonos facetados de sombreamento chapado, geometria mínima, cores sólidas, sol laranja suave vindo da esquerda.

## 8. Quadrinhos / graphic novel (graphic novel)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: ação, noir, suspense, tom adulto, histórias de herói autoral. Nunca personagem, editora ou desenhista de terceiros.
- Palavras do prompt (EN): abertura `graphic novel panel of` · âncora `heavy ink linework, halftone dot shading, cross-hatching, black and white with <1 ou 2 cores de destaque> spot color`.
- Parâmetros V8.2 (ponto de partida): `--s 100-200`. Aqui o `--no text, speech bubble, panel border` entra desde o primeiro prompt: o Midjourney costuma gerar balões e texto ilegível nesta estética.
- Paleta e luz: preto chapado, 1 ou 2 cores de destaque; luz dura, sombras fortes, alto contraste.
- Consistência: a espessura do traço e o padrão da retícula ficam na âncora; personagem com silhueta forte (chapéu, casaco, cabelo).
- Imagem → vídeo: sobrevivência baixa. Riscos: retícula e hachura tremulam, a tinta "escorre". Como reduzir: câmera parada e movimento mínimo, ou tratar como quadrinho animado (camadas com paralaxe na edição).
- Descritor para o vídeo (sugestão): 图像小说风格，粗墨线，网点阴影 (estilo graphic novel, traço de tinta grosso, sombra em retícula).
- Exemplo:
  `Graphic novel panel of a detective in a long trench coat standing under a flickering streetlight in heavy rain, face half in shadow, heavy ink linework, halftone dot shading, cross-hatching, black and white with red spot color --s 150 --ar 9:16 --no text, speech bubble, panel border`
  Tradução: quadro de graphic novel: um detetive de sobretudo longo debaixo de um poste piscando, chuva forte, metade do rosto na sombra; traço de tinta grosso, sombra em retícula, hachura cruzada, preto e branco com destaque em vermelho.

## 9. Ilustração pintada / aquarela (watercolor, painted illustration)
- Estado: ativa · Testada em: ainda não (heurística a confirmar)
- Quando usar: memória, poesia, infância, afeto, contemplação, livro ilustrado.
- Palavras do prompt (EN): abertura `watercolor illustration of` · âncora `wet-on-wet bleeds, visible paper grain, pigment granulation, soft edges, white paper showing through, <paleta lavada>`. Variante pintura opaca (a testar): `gouache illustration of ... visible brush strokes, matte opaque paint`.
- Parâmetros V8.2 (ponto de partida): `--s 150-300`; testar com e sem `--raw`.
- Paleta e luz: tons lavados; o branco do papel faz a luz; poucos pretos.
- Consistência: a textura do papel e a intensidade das manchas iguais em toda a série; rostos simples, com poucos traços.
- Imagem → vídeo: sobrevivência baixa. Riscos: a textura do papel "gruda" nos objetos em movimento; as manchas pulsam. Como reduzir: câmera parada, movimentos lentos.
- Descritor para o vídeo (sugestão): 水彩风格 (estilo aquarela).
- Exemplo:
  `Watercolor illustration of a grandmother and a small boy sitting on a porch swing at dusk, fireflies over a yard of tall grass, wet-on-wet bleeds, visible paper grain, pigment granulation, soft edges, white paper showing through, muted warm palette --s 200 --ar 9:16`
  Tradução: ilustração em aquarela: avó e menino pequeno num balanço de varanda ao anoitecer, vaga-lumes sobre o quintal de mato alto; manchas molhado sobre molhado, textura do papel visível, granulação do pigmento, bordas suaves, o branco do papel aparecendo, paleta quente e lavada.

## Fichas novas
As estéticas novas entram abaixo desta linha, no modelo da SKILL.md, com o estado "em teste" até o "aprovado" do José.

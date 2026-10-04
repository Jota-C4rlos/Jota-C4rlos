---
name: esteticas
description: Catálogo de estéticas do pilar visual (hiper-realista, 3D de animação, 2D cartoon, anime, pixel art, claymation, low-poly, quadrinhos, aquarela) - quando usar, como escrever no Midjourney, como manter a consistência e o risco de cada uma na passagem de imagem para vídeo. Use ao propor a estética de um projeto e ao escrever prompts numa estética escolhida.
user-invocable: false
---
# Estéticas

Cada estética tem um jeito de trabalhar: as palavras do prompt, os parâmetros, a luz, a paleta e o que quebra quando a imagem vira vídeo. A ficha de cada uma está em .claude/skills/esteticas/catalogo-esteticas.md. Leia a ficha antes de escrever qualquer prompt na estética.

Atenção: as dicas de prompt, os parâmetros sugeridos e a avaliação de risco imagem → vídeo são heurísticas de prática, não verificadas em fonte. A pesquisa de 2026-10-04 não conseguiu abrir as páginas e não achou teste publicado dessas estéticas no Seedance ou no Kling. Use como ponto de partida. O que se confirma vem dos testes do José: o resultado vira linha no caderno do visual e, na retrospectiva, atualização desta skill.

## O catálogo
| Estética | Serve para | Imagem → vídeo (heurística) |
|---|---|---|
| Hiper-realista / cinematográfico | drama, suspense, cotidiano, produto real, documental | alta sobrevivência; rosto muda em giro de cabeça, mãos, estranheza em close |
| 3D de animação | fábula, humor, família, animais e objetos que falam, mascote | alta; rosto "derrete" em movimento rápido, olhos mudam de tamanho |
| Claymation / stop-motion | humor artesanal, infantil, nostalgia | alta no material; perde o ritmo "aos pulos" |
| Anime (2D cel) | ação, emoção intensa, fantasia, público jovem | média; vira 2.5D, as linhas tremem |
| Low-poly | tecnologia, jogo, explicação, diorama | média; as facetas se suavizam |
| 2D cartoon (flat / vetor) | explicativo, humor simples, marca | baixa; ganha volume e luz, contornos "respiram" |
| Quadrinhos / graphic novel | ação, noir, suspense, tom adulto | baixa; retícula e hachura tremulam |
| Ilustração pintada / aquarela | memória, poesia, infância, contemplação | baixa; a textura do papel "gruda" nos objetos |
| Pixel art | games, nostalgia, retrô | muito baixa; a interpolação borra a grade de pixels |

Quanto mais baixa a sobrevivência, mais o projeto precisa de câmera parada, ações simples e takes curtos, ou de um acabamento na edição (um filtro de pixelização, por exemplo). Outras estéticas que podem virar ficha: papel recortado (sobrevive bem, como o claymation), noir em preto e branco, filme analógico (o grão sobrevive bem) e 3D com acabamento de pintura (risco médio).

## Como escolher as 2 ou 3 opções
1. Leia o tom, o público e a plataforma no briefing; o tom e a função das cenas no roteiro; a estética sugerida no conceito.
2. Pese cada estética do catálogo por cinco critérios:
   - serve à história e ao tom;
   - sobrevive à passagem para o vídeo no modelo escolhido (coluna da tabela);
   - consistência: quantos personagens e cenários recorrentes, quantos quadros;
   - os riscos do roteiro (portas, mãos, ação rápida, 3 ou mais personagens) somados aos da estética;
   - direitos: a estética se descreve pelas características, nunca pelo nome de um estúdio ou artista.
3. Se o briefing já traz uma estética, ela é a opção A; as outras são variações dela (outra luz, outra paleta, mais ou menos estilizada) ou uma alternativa mais segura para o vídeo.
4. Estética de sobrevivência baixa ou muito baixa só entra com o plano de mitigação escrito e com uma alternativa de sobrevivência alta ao lado.
5. Cada opção leva: justificativa, abertura e âncora de estilo, parâmetros, risco imagem → vídeo e um prompt de teste com um quadro-chave do roteiro (modelo do entregável no agente visual).

## Âncora de estilo
O V8 é literal: o que o prompt não diz sai na estética padrão do modelo. Por isso cada projeto tem uma âncora de estilo, em inglês, colada igual, palavra por palavra, em todo prompt do projeto.
- Abertura (estilizadas): o meio abre o prompt. Ex.: `2D cel-shaded anime still of`.
- Âncora (todas): fecha o texto, antes dos parâmetros: textura ou traço, regra de luz, paleta. Ex.: `clean lineart, flat cel colors, hard-edged shadows, warm orange backlight, palette of teal, coral and cream`.
- Hiper-realista: o prompt abre pelo sujeito; a âncora traz câmera, filme e grão (a lente muda com o plano e vai junto do enquadramento).
- Parâmetros da série: os mesmos em toda imagem (`--raw` ou não, `--s`, `--exp`, `--sref`, `--p`). Só o `--ar` muda com o tipo de imagem.

## Paleta e luz
- Paleta-mestra do projeto: 4 a 6 cores com nome ("terracotta, faded teal, warm cream"). Cada personagem e cenário tira a sua paleta dela.
- Personagens que contracenam têm figurinos de cores diferentes entre si e diferentes do fundo (heurística: ajuda o modelo de vídeo a não trocar um pelo outro, e o José a conferir quem é quem).
- Luz: uma regra por cenário (hora, fonte, de que lado vem). A direção da luz não muda entre quadros do mesmo cenário, porque isso quebra a continuidade no vídeo.

## Consistência em qualquer estética
- Bloco-âncora de cada personagem e cenário e a tag curta de cada personagem, idênticos em todo prompt (skill midjourney).
- A mesma âncora de estilo e os mesmos parâmetros em toda a série; `--exp` em 0; `--s` dentro da faixa da ficha.
- Referências aprovadas no Edit Model em cada quadro.
- Nas estilizadas, o maior inimigo é a deriva de proporção: tamanho da cabeça em relação ao corpo, tamanho dos olhos, espessura da linha. Escreva a proporção na ficha do personagem (ex.: "cabeça grande, 1/4 da altura") e confira no parecer.

## Da imagem ao vídeo (todas as estéticas)
Heurísticas, a confirmar nos takes do José:
- A imagem do Midjourney é o primeiro quadro do take ou a referência dele, na mesma proporção do vídeo.
- O pilar prompts repete o descritor de estilo no prompt de vídeo. Cada ficha traz uma sugestão em mandarim; a redação final é dele.
- Uma ação principal por take.
- Nas estéticas 2D, câmera estável.
- Giro de 180° do personagem só com a referência de costas (turnaround).
- Revise cada take procurando deriva de rosto, mãos, figurino e paleta antes de aprovar.

## Como acrescentar uma estética nova
Quem faz é o pilar skills. Só vale depois do "aprovado" do José.
1. Pedido: o José pede, ou um projeto precisa de uma estética fora do catálogo (o pilar visual avisa em PENDENCIAS).
2. Pesquisa: como a estética se descreve (meio, traço, textura, luz, paleta), com fonte e data. Nada de nome de estúdio, marca ou artista vivo nas palavras do prompt.
3. Ficha no modelo abaixo, no fim de catalogo-esteticas.md, com o estado "em teste".
4. Teste: um prompt de personagem e um de cenário. O José gera no Midjourney e, se quiser, um take curto no modelo de vídeo (gasta créditos: só com a aprovação dele).
5. O pilar visual dá o parecer das imagens: a estética se repete? Bate com a ficha? Como ficou no vídeo?
6. Ajustes na ficha, estado "ativa" e uma linha na tabela "O catálogo" desta skill.
7. Registro em _Sistema/licoes/changelog.md e data atualizada em _Sistema/academia/catalogo.md.

Modelo de ficha:
```markdown
## N. <Nome em português> (<nome em inglês>)
- Estado: ativa | em teste · Testada em: <projeto, data, resultado>
- Quando usar: <tom, gênero, público>; quando evitar: <...>
- Palavras do prompt (EN): abertura `<...>` · âncora `<...>`
- Parâmetros V8.2 (ponto de partida): `<...>`
- Paleta e luz: <...>
- Consistência: <o que deriva e como travar>
- Imagem → vídeo: sobrevivência <alta, média, baixa> · riscos: <...> · como reduzir: <...>
- Descritor para o vídeo (mandarim, sugestão): <...> (<tradução>)
- Exemplos (EN, com tradução): <1 ou 2 prompts curtos>
```

## Fontes
Pesquisa do Orquestrador em 2026-10-04, feita por trechos de busca, sem leitura completa das páginas.
- Regras de prompt e parâmetros do Midjourney V8.2: skill midjourney e https://docs.midjourney.com/hc/en-us/articles/32859204029709-Parameter-List (verificado em ago. de 2026).
- Niji 7 fora do V8 e `--niji` incompatível: https://docs.midjourney.com/hc/en-us/articles/32199405667853-Version (verificado em ago. de 2026).
- Fichas das estéticas e sobrevivência imagem → vídeo: heurísticas de prática reunidas na pesquisa, sem fonte verificada; a confirmar com testes no Seedance e no Kling.
- Proporções aceitas pelo Seedance 2.5 (16:9, 4:3, 1:1, 3:4, 9:16, 21:9): https://docs.byteplus.com/en/docs/ModelArk/2607688 (ago. de 2026).
- Relatos de deriva de figurino e de identidade com 3 ou mais personagens no Seedance 2.5: https://www.kapwing.com/resources/is-seedance-2-5-actually-better-than-2-0-heres-what-i-found/ (ago. a set. de 2026, terceiro, confiança baixa).

Se a ferramenta mudou, peça ao pilar skills a atualização.

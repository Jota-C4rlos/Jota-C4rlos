# Modelos dos entregáveis do pilar prompts

Modelos da skill metodo-take. Caminhos relativos à pasta do projeto. Nomes de arquivo em minúsculas, sem acento, com a versão no fim.

## 04_Prompts/plano-takes_vNN.md

```markdown
# Plano de takes — <projeto> · v01
Roteiro: 02_Roteiro/roteiro_v02.md · Visual: 03_Visual/cenarios_v01.md, storyboard_v01.md · Método: metodo-take (rascunho)
Modelo: Seedance 2.5 · Proporção: 9:16 · Resolução: 1080p
Respostas do José: fala gerada no take (PT-BR) · música na edição (pilar 6) · sem legenda · takes de até 30 s
Total: 5 takes · 60 s somados · roteiro: 60 s

## Mapa de tags
| Tag do projeto | Arquivo | Papel (o que a imagem define) | Takes |
|---|---|---|---|
| personagem-davi | 03_Visual/imagens/personagem-davi-corpo_01.png | rosto, cabelo e figurino do Davi (camisa azul) | 01–05 |
| personagem-leo | 03_Visual/imagens/personagem-leo-corpo_01.png | rosto, cabelo e figurino do Léo (jaqueta preta) | 01–05 |
| cenario-escritorio | 03_Visual/imagens/cenario-escritorio-mestre_01.png | layout, porta e luz do escritório | 01–02 |
Símbolos reservados: (música) · <efeito> · {fala} · 【texto na tela】.

## Mapa da cena (de cenarios_v01.md)
| Local | Porta: parede · dobradiça · abre para · de dentro · de fora | Janelas e luz | Saídas | Lado da câmera (eixo) |
|---|---|---|---|---|
| escritório | fundo · direita · dentro da sala · puxa · empurra | janela à esquerda, tarde | porta do fundo → corredor à esquerda | dentro da sala, de frente para o fundo |

## Bíblia de continuidade (colada igual em todos os takes)
- 蓝衬衫男人，三十岁左右，黑色短发，浅蓝色衬衫，深灰色长裤。 — Davi: camisa azul-clara, calça cinza-escura.
- 黑夹克男人，四十岁左右，寸头，黑色皮夹克，黑色长裤。 — Léo: jaqueta de couro preta, calça preta.
- Estética (o descritor para o vídeo da estetica_v02.md): 写实电影质感，自然光，柔和的暖色调。 — cinema realista, luz natural, tons quentes.

## Takes
| Take | Tempo no vídeo | Duração | Cenas | Quadros do storyboard | Ponte de entrada |
|---|---|---|---|---|---|
| take-01 | 00:00–00:18 | 18 s | 1 | quadro-01, quadro-02 | — |
| take-02 | 00:18–00:30 | 12 s | 2 | quadro-03 | corte com redeclaração |

### take-02 · 00:18–00:30 · 12 s
- Cenas: 2 (do "Corte:" até a saída pela porta)
- Personagens: Davi à esquerda, mais perto da porta; Léo à esquerda, de costas para a janela. Saem: Davi primeiro, Léo atrás.
- Cenário: escritório. Porta no fundo, dobradiça à direita, abre para dentro da sala (de dentro: puxa). Janela à esquerda; tarde.
- Referências, nesta ordem: 1. personagem-davi-corpo_01.png → @图片1 · 2. personagem-leo-corpo_01.png → @图片2 · 3. cenario-escritorio-mestre_01.png → @图片3
- Áudio: sim. Fala do Léo em PT-BR {Vamos. Antes que ele volte.} · efeitos <maçaneta> <dobradiça> <passos> · sem música.
- Tags e símbolos: @图片1–3 · {} · <>
- Estado inicial: os dois junto à mesa, à esquerda; porta fechada.
- Estado final: escritório vazio; porta aberta para dentro, parada à direita do vão; no corredor, Davi na frente e Léo atrás, indo para a esquerda.
- Ponte para o take-03: corte com redeclaração (接上一镜), mesma direção de tela (direita → esquerda).
- Risco: porta (alto). Saída já aplicada: direção de abertura escrita, porta fica aberta, regra em 限制.
```

## 04_Prompts/takes_vNN.md

```markdown
# Takes — <projeto> · v01
Modelo: Seedance 2.5 · 9:16 · 1080p · Plano: plano-takes_v01.md · Revisão: revisao_v01.md

| Take | Prompt | Duração | Tipo de tarefa | Mudou nesta versão |
|---|---|---|---|---|
| take-01 | v01 | 18 s | referência multimodal | — |
| take-02 | v01 | 12 s | referência multimodal | — |

## take-02 · prompt v01 · 12 s
Configuração: Seedance 2.5 · referência multimodal · 12 s · 9:16 · 1080p · áudio ligado
Subir nesta ordem: 1. 03_Visual/imagens/personagem-davi-corpo_01.png · 2. 03_Visual/imagens/personagem-leo-corpo_01.png · 3. 03_Visual/imagens/cenario-escritorio-mestre_01.png
Salvar como: 05_Geracao/takes/take-02_t01.mp4 (t02, t03... nas tentativas seguintes)

### Prompt
(o prompt em mandarim, num bloco de código, pela estrutura do metodo-take)

### Tradução
(fiel, bloco a bloco)

### Notas de direção
- O que conferir: a porta abre na direção da câmera; Davi sai primeiro.
- Se errar a porta: peça o ajuste dizendo em que segundo e para que lado ela abriu.
```

Num ajuste, o take mudado ganha a versão nova e, logo abaixo do título:
```markdown
## take-02 · prompt v02 · 12 s · AJUSTE
Ajuste v02: na saída, a porta abriu para o corredor (take-02_t01.mp4, aos 6 s).
Antes → depois: "把门朝自己、朝镜头方向拉开。" → "向后退一步，把门朝自己、朝镜头方向拉开，门板向室内转开。" · em 限制, + "门不能向走廊方向打开"
Resto do prompt: igual ao v01, palavra por palavra. O prompt completo vem logo abaixo, em "### Prompt", pronto para colar.
Ponte com o take-03: sem mudança. (Ou: ⚠️ muda o estado inicial do take-03 — <qual mudança>; decisão do José.)
```
Os takes que não mudaram são copiados sem nenhuma alteração e mantêm a versão de prompt que tinham (take-01 continua v01 dentro do takes_v02.md). A versão de cada take é a do arquivo em que ele mudou pela última vez; é ela que vai para a coluna Prompt da tabela Takes do status.md.

## 04_Prompts/ajustes.md (arquivo de controle: só recebe linhas)

```markdown
# Ajustes dos takes — <projeto>

| Data | Take | Erro relatado | O que mudou | Versão |
|---|---|---|---|---|
| 2026-10-12 | take-02 | na saída, a porta abriu para o corredor (t01, 6 s) | só a frase da porta em 4–8秒 e 1 restrição em 限制 | takes_v02 · take-02 v02 |
```

## 05_Geracao/conferencia_vNN.md (quando o José pedir)

```markdown
# Conferência dos takes gerados — <projeto> · v01
Takes conferidos: take-01_t02.mp4, take-02_t01.mp4 · Quadros em 05_Geracao/conferencia/

## Ponte take-01 → take-02 · conferencia/ponte_take-01-02.png
✅ Posições: nos dois quadros, os dois junto à mesa, à esquerda, Davi mais perto da porta.
⚠️ Figurino: a jaqueta do Léo está aberta no fim do take-01 e fechada no início do take-02. Correção sugerida: no take-02, "黑色皮夹克敞开着" em 主体. (Ajuste só se o José pedir.)

## Resumo
2 pontes · 1 ✅ · 1 ⚠️
```

## Biblioteca/prompts/<nome-curto>.md (take que funcionou de primeira)

```markdown
# <nome-curto> — take que funcionou de primeira
Modelo e versão: Seedance 2.5 · tipo de tarefa: referência multimodal · 12 s · 9:16 · data: AAAA-MM-DD
Projeto de origem: <nome curto, sem dados do cliente>

## A cena
(o que acontece, em português, 2 a 3 linhas)

## Prompt
(o prompt em mandarim)

## Tradução

## Referências usadas
(tipo e papel de cada uma; sem as imagens do cliente)

## Por que funcionou
(o que segurou a continuidade e a física: geografia declarada, ação com direção, restrição no fim...)
```

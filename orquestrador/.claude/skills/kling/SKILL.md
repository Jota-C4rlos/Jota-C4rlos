---
name: kling
description: Método Kling - regras e limites do Kling (Kuaishou), a alternativa ao Seedance no pilar prompts - versões 3.0 (estável) e 4.0 (anunciado), fórmula oficial, multi-shot, Elements e consistência, primeiro e último quadro, falas, falhas conhecidas e como adaptar um take escrito para o Seedance. Use quando a OS trouxer MÉTODO kling.
user-invocable: false
---
# Kling (método Kling)

O Kling, da Kuaishou, é a alternativa ao Seedance. O José chamou de "método Kling": as regras do modelo e o jeito de levar um take do método Take para ele. A estrutura do take continua sendo a do metodo-take; esta skill diz o que muda. Fonte: pesquisa de 2026-10-04 por trechos de busca. Confiança alta vira regra; o resto está marcado **a confirmar**.

## 1. Versões em 2026-10-04
- **Kling 3.0** é o estável, lançado em 05/02/2026: Video 3.0 e Video 3.0 Omni (e Image 3.0 e Image 3.0 Omni). É o que se usa hoje.
- **Kling 3.0 Turbo**: saiu em 17/06/2026, segundo terceiros; a duração máxima não foi publicada (**a confirmar**).
- **Kling 4.0**: anunciado em 28/09/2026, com lançamento completo "em outubro de 2026", sem data exata. Hoje só o **4.0 Flash** está ativo, em acesso antecipado limitado (assinantes Ultra anuais): até 20 s, até 720p, 8-bit SDR, texto → vídeo, imagem → vídeo e Omni Reference.
- Quando o 4.0 completo sair e o José tiver acesso, peça ao pilar skills a atualização desta skill.

## 2. Ficha técnica
| Item | Kling 3.0 (estável) | Kling 4.0 (anunciado, **a confirmar**) |
|---|---|---|
| Duração por geração | 3 a 15 s | 3 a 30 s (o Flash, já ativo: até 20 s, confirmado) |
| Resolução | 720p e 1080p (a página de recursos cita 4K) | 720p, 1080p e 4K; HDR 10-bit "ainda chegando" |
| Proporção | 16:9, 9:16, 1:1 | 16:9, 9:16, 1:1, 21:9 e Smart |
| Áudio | nativo | estéreo |
| Falas | inglês, chinês, japonês, coreano e espanhol; **sem português** | lip-sync em 9 idiomas, português incluído |
| Multi-shot | até 6 planos | até 10 keyframes; o limite de 6 planos pode mudar |
| Referências | Elements: até 4 imagens, vídeo de 3 a 8 s, voz de 5 a 30 s (**a confirmar**) | Omni Reference até 15 itens: 10 imagens + 5 vídeos (até 30 s), até 7 sujeitos, 3 a partir de vídeo, mais voz |
| Extensão | guia antigo: 4 a 5 s por vez, até 3 min (**a confirmar**) | até 2 min, "em breve" |

O 3.0 faz diálogo com vários personagens, cada um no seu idioma, controlando quem fala e em que ordem; entende campo e contracampo e montagem paralela. O 3.0 Omni tem storyboard com duração, enquadramento, ângulo e movimento por plano. A ficha do 3.0 vem de fonte com mais de 6 meses.

## 3. Fórmula oficial
**Sujeito (descrição) + Movimento do sujeito + Cena (descrição) + (Linguagem de câmera + Iluminação + Atmosfera)**.
- Fala: amarre cada fala ao personagem e diga o tom e o ritmo. Exemplo oficial: `Mom (softly, in a surprised tone): "..."`. Dialeto ou sotaque podem ser pedidos no prompt.
- Luz com direção fixa ("from camera left", "from camera right"). Não combine instruções opostas, como luz suave e difusa com sombras duras e recortadas.

## 4. Multi-shot
- Na interface: `Shot 1 (3s): ...; Shot 2 (2s): ...`. Na API: `shot n, m, words;`, com n de 1 a 6, m de pelo menos 1 s, e a soma das durações igual à duração total (**a confirmar**: guia oficial lido só em trecho).
- Exemplo oficial: `Shot 1 (3s): Wide shot. A neon-lit street corner late at night... @Element1 leans against a red phone booth...; Shot 2 (2s): Cut to close-up. @Element1's profile is half-hidden in shadow... asks, "You still haven't decided which road to take?"`
- Boas práticas oficiais: defina a cena antes da decupagem; escreva na ordem dos planos; diga a cobertura de cada plano; ligue cada fala ao personagem; **um movimento de câmera principal por plano**. Empilhar "push in, pan left, tilt up, rotate, zoom, follow" gera instabilidade.
- Relatos de terceiros: a consistência cai perto do 4º ou 5º plano. Num take com muitos planos, prefira dividir em dois takes.

## 5. Elements e consistência de personagem
- Elements (subject binding): a chave "Bind Subject to Enhance Consistency" fixa rosto, roupa e voz (**a confirmar**: até 4 imagens de referência, vídeo de 3 a 8 s, voz de 5 a 30 s).
- Tags: na interface, `@Element1`; na API do Omni, `<<<element_1>>>`, `<<<image_1>>>`, `<<<video_1>>>`, `<<<voice_1>>>`.
- No 4.0 (orientação oficial, **a confirmar**): os keyframes dizem QUANDO algo muda; o Omni Reference diz O QUE fica igual. Só use keyframe quando o estado visual muda de verdade.

## 6. Primeiro e último quadro, extensão
- As duas imagens precisam ser parecidas: diferença grande vira corte de câmera.
- Na extensão, mantenha no prompt o sujeito e o movimento do clipe original.
- A API tem campo de prompt negativo, até 2.500 caracteres. Na interface do José, **a confirmar**.
- Fonte antiga (mais de 6 meses): pode não valer para o 3.0 e o 4.0.

## 7. Falas em português
O Kling 3.0 não fala português. Para um take com fala em PT-BR, o José escolhe:
1. Gerar sem fala (só ambiente e efeitos) e pôr a voz na edição (dublagem com ElevenLabs, por exemplo).
2. Trocar a fala por ação, se o roteiro permitir (pergunta ao José, via PENDENCIAS).
3. Esperar o 4.0, que anuncia português (**a confirmar** no lançamento).
4. Gerar esse take no Seedance 2.5, que aceita fala em outro idioma quando ele é declarado antes (a qualidade em português: **a confirmar** no primeiro take com fala).

## 8. Idioma do prompt
A regra da casa é mandarim. A pesquisa não confirmou se o Kling rende mais em chinês ou em inglês; os guias oficiais citados estão em inglês. Os rótulos e exemplos oficiais (`Shot 1 (3s):`, `@Element1`) estão em inglês. Use o rótulo oficial `Shot 1 (3s):`, com o texto de cada plano em mandarim. `镜头1（3秒）：` só como teste A/B (**a confirmar**): se o Kling respeitar os cortes, o pilar skills atualiza esta regra. Se o José quiser tirar a dúvida, o pilar skills faz um teste A/B com o mesmo take nas duas línguas.

## 9. Falhas conhecidas
Relatos de terceiros sobre o 3.0 (confiança baixa; **a confirmar** nos takes do José):
- mãos e dedos;
- física de contato (uma bola que "teletransporta");
- inconsistência perto do 4º ou 5º plano;
- degradação em extensões encadeadas depois de 30 a 60 s;
- lip-sync instável com mais de 3 falantes.
Líquidos e partículas (água, vapor, chuva) foram elogiados. A prevenção está na skill continuidade-e-fisica.

## 10. Adaptar um take do Seedance para o Kling
1. **Duração**: o teto do 3.0 é 15 s. Take maior vira dois, com ponte (estado final do primeiro = estado inicial do segundo) e o plano de takes atualizado.
2. **Estrutura**: mantenha os blocos do metodo-take e mapeie para a fórmula do Kling: 主体 → sujeito; 时间线 (ações) → movimento do sujeito; 场景与环境 → cena; 视觉风格 + câmera + luz → o parêntese final da fórmula (câmera, iluminação, atmosfera).
3. **Linha do tempo → planos**: cada trecho `0–4秒：` que tem corte vira `Shot 1 (4s):`, na ordem, no máximo 6, com a soma igual à duração. Plano-sequência sem corte fica num plano só.
4. **Referências**: as tags @图片N viram Elements (`@Element1`) com o personagem vinculado. Papel estreito para cada uma, como no Seedance.
5. **Som e texto**: os símbolos (), <>, {} e 【】 são do Seedance. No Kling: fala com o personagem, o tom entre parênteses e a fala entre aspas; música e efeitos descritos em palavras; texto na tela vai para a edição.
6. **Falas**: em português, siga a seção 7.
7. **Restrições**: se houver campo negativo, mova as restrições para lá; senão, deixe no fim do prompt.
8. **Continuidade**: a geografia (porta, dobradiça, lado de abertura), as posições e a direção de tela vão iguais. Um movimento de câmera por plano e a luz com direção fixa.
9. Registre no takes_vNN.md "Modelo: Kling 3.0" e a configuração (duração, proporção, resolução, Elements).

Exemplo curto (trecho do take do metodo-take, seção 5, convertido; a fala em português sai do take):
```text
Shot 1 (4s): 中景，固定机位。@Element2 黑夹克男人看着 @Element1 蓝衬衫男人，压低声音说话，蓝衬衫男人点头。
Shot 2 (8s): 同一机位。蓝衬衫男人走到门的左侧，用右手把门朝自己、朝镜头方向拉开，门绕右侧铰链向室内转开；他先走进走廊，向画面左侧走去，黑夹克男人跟在后面。门保持敞开。
```
> Plano 1 (4 s): plano médio, câmera fixa. O de jaqueta preta olha para o de camisa azul e fala baixo; o de camisa azul faz que sim. Plano 2 (8 s): mesma câmera. O de camisa azul vai ao lado esquerdo da porta, puxa a porta para si com a mão direita, na direção da câmera; a porta gira na dobradiça da direita para dentro da sala; ele sai primeiro pelo corredor, para a esquerda do quadro, e o de jaqueta preta vai atrás. A porta fica aberta.

A fala ("Vamos. Antes que ele volte.") entra na edição. O cenário, o estilo e as restrições vêm antes e depois, como no take original.

## Fontes
Pesquisa do Orquestrador em 2026-10-04, por trechos de busca:
- Kling 4.0 e 4.0 Flash: https://kling.ai/dev/model-release/kling-4 (28/09/2026).
- Especificações anunciadas do 4.0: https://kling.ai/blog/kling-4-vs-3 (28 a 30/09/2026, confiança média).
- Kling 3.0: https://ir.kuaishou.com/news-releases/news-release-details/kling-ai-launches-30-model-ushering-era-where-everyone-can-be/ (05/02/2026).
- Fórmula do prompt: https://kling.ai/quickstart/klingai-video-3-model-user-guide (fev. 2026).
- Multi-shot e tags do Omni: https://kling.ai/quickstart/klingai-video-3-omni-model-user-guide (fev. a mar. 2026, confiança média).
- Boas práticas de multi-shot: https://kling.ai/blog/kling-video-3-multi-shot-guide (2026).
- Elements: https://kling.ai/blog/kling-3-subject-binding-character-consistency (2026, confiança média).
- Primeiro e último quadro, extensão: https://kling.ai/quickstart/ai-video-start-end-frames (anterior a 2026, confiança média).
- Falhas: https://magichour.ai/blog/kling-30-review (2026, terceiro, confiança baixa).

Se a ferramenta mudou, peça ao pilar skills a atualização.

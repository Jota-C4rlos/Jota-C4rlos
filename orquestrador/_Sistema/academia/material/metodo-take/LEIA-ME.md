# Material do método Take

Esta pasta guarda o seu método Take: a estrutura dos prompts de vídeo e os cerca de 20 prompts de exemplo em mandarim. É com eles que o pilar prompts aprende a escrever do seu jeito. Enquanto o material não chega, a skill metodo-take fica em rascunho, com uma estrutura provisória montada sobre o guia oficial do Seedance 2.5.

No Windows, a pasta é `_Sistema\academia\material\metodo-take\`, dentro da pasta do vault.

## O que colocar aqui
Mandou tudo num arquivo só? Também serve: o pilar skills separa.

1. **A estrutura do Take**: como você monta um prompt, bloco por bloco, e as tags que usa. Pode ser um texto, um print, um PDF ou um áudio explicando. Se a estrutura veio de um curso ou de outro criador, diga de onde (nome, perfil ou link): não achamos nada público com o nome "método Take".
2. **Os prompts de exemplo**, em mandarim, do jeito que você colou na plataforma. Para cada um, se souber (só o prompt já serve; o resto ajuda):
   - **A cena**: o que acontece, em português, em 2 ou 3 linhas.
   - **Modelo e versão**: Seedance 2.5, Seedance 2.0, Kling 3.0...
   - **Duração** do take, em segundos.
   - **Funcionou?** Sim, não ou em parte.
   - **O que deu errado**: a porta, quem saiu primeiro, o rosto, as mãos, a fala... e em que segundo. Se precisou ajustar, cole também o prompt que corrigiu.
3. **Opcional**, e ajuda muito: o vídeo gerado de cada exemplo e as imagens de referência que você subiu, com o mesmo número do exemplo.

## Como organizar
Um arquivo por exemplo, numerado. Texto em .md ou .txt, vídeo e imagens com o mesmo começo de nome:
```
estrutura-take.md
exemplo-01_dois-homens-saem-pela-porta.md
exemplo-01_dois-homens-saem-pela-porta.mp4
exemplo-01_ref-01.png
exemplo-02_...
```
Modelo para cada exemplo:
```
# Exemplo 01 — <título curto>
Cena: <o que acontece, em português>
Modelo e versão: <Seedance 2.5>
Duração: <12 s>
Funcionou: <sim / não / em parte>
O que deu errado: <ex.: aos 7 s, a porta abriu para o corredor>

## Prompt (mandarim)
<cole aqui>

## Prompt corrigido (se houver)
<cole aqui>
```
Nomes em minúsculas, sem acento, com hífen entre palavras.

## Fica só no seu computador
O `.gitignore` deixa tudo desta pasta fora do git, menos este LEIA-ME. O método é seu: os exemplos inteiros não sobem para o repositório. A skill que sair daqui resume a estrutura e as regras, com 2 ou 3 exemplos curtos (só com a sua permissão) e um índice dos exemplos (número, a cena em poucas palavras e o nome do arquivo, sem o prompt), que o pilar prompts usa para achar o exemplo certo.

## Como pedir
Com o material na pasta, diga ao orquestrador: **"abra o curso do método Take"**.
1. O orquestrador avisa o custo estimado antes de começar.
2. O pilar skills lê a estrutura e os exemplos e reescreve a skill metodo-take: a sua estrutura no lugar da provisória, as suas tags e as regras tiradas do que funcionou e do que deu errado. O pilar prompts faz um exercício com uma cena nova.
3. Você revisa e aprova. Só então o catálogo marca a skill como ativa.

Mandou mais exemplos depois, ou mudou a estrutura? Peça a atualização da skill do método Take. Os takes que funcionarem de primeira nos projetos também viram exemplo (Biblioteca/prompts/).

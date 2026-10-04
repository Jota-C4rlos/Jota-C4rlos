---
name: ideia
description: Guarda no Box de Ideias uma ideia, um roteiro solto, um áudio, um arquivo ou um link, com as palavras do José intactas, e registra no índice. Use quando o José digitar /ideia ou pedir para guardar uma ideia.
argument-hint: texto, link, áudio ou arquivo da ideia
---
# /ideia — guardar uma ideia no Box

Você mesmo faz, sem delegar. É uma captura rápida: o José está guardando, não desenvolvendo.

## Regra de ouro
As palavras do José entram como ele disse: sem corrigir, resumir, melhorar ou traduzir. Comentário seu fica fora da seção "A ideia" e vai marcado "(Claude)".

## Passos
1. **Entrada.** Sem nada depois de /ideia, pergunte só: "Qual é a ideia?". Várias ideias na mesma mensagem viram uma nota cada; na dúvida se é uma ou várias, pergunte.
2. **Já existe?** Procure no Box_de_Ideias/indice.md (títulos e tags) algo parecido. Se for variação de uma ideia guardada, pergunte: "Junto em Variações da ide-NNN ou guardo como nova?" (sugestão: juntar). Juntar é acrescentar uma linha em "Variações" da nota existente, com a data.
3. **Id e nome.** Próximo id da tabela Ideias (o maior + 1; a primeira é ide-001). Título curto, de 2 a 6 palavras, tirado das palavras do José. Arquivo: `Box_de_Ideias/ideias/AAAA-MM-DD_<titulo>.md` (data de hoje; minúsculas, sem acento, hífen entre palavras). Se o nome já existir, acrescente `-2`.
4. **Nota.** Copie _Sistema/templates/ideia.md e preencha:
   - Frontmatter: id, data, titulo, tipo (o que o José disse; senão `a definir`), tags (de 2 a 5, se forem óbvias; senão `[]`), status `nova`, origem.
   - Título da nota (`# ...`) igual ao titulo.
   - "A ideia", conforme o que veio:

   | Veio | O que fazer | origem |
   |---|---|---|
   | texto | cole na íntegra | José (texto) |
   | roteiro solto | cole na íntegra; se passar de uma página, copie o arquivo para Box_de_Ideias/ideias/ com o mesmo nome da nota e ponha o link | José (roteiro) |
   | áudio | copie o arquivo para Box_de_Ideias/ideias/ com o mesmo nome da nota (extensão original), ponha o link e escreva "transcrição pendente" | José (áudio) |
   | vídeo do José (ele contando a ideia) | copie para Box_de_Ideias/ideias/ com o mesmo nome da nota (extensão original), ponha o link e escreva "transcrição pendente"; não é referência: não vai para o /dna | José (vídeo) |
   | arquivo (imagem, PDF, documento) | copie para Box_de_Ideias/ideias/ com o mesmo nome da nota e ponha o link; se for texto, cole também o conteúdo | José (arquivo) |
   | link | o link e o que o José disse sobre ele | José (link) |

   - Copie, nunca mova: o original do José fica onde está.
   - Nas outras seções, só o que o José disse (por que pode funcionar, variações, perguntas). O resto fica vazio, para quando a ideia for trabalhada.
5. **Índice.** Se Box_de_Ideias/indice.md não existir (ele fica fora do git), crie-o a partir de _Sistema/templates/indice-box.md. Acrescente uma linha ao final da tabela Ideias:
   ```
   | ide-NNN | AAAA-MM-DD | <título> | <tipo> | <tags> | nova | <origem> | Box_de_Ideias/ideias/AAAA-MM-DD_<titulo>.md |
   ```
6. **Link de vídeo.** Ofereça o DNA: "Quer o DNA desse vídeo?". Se o José disser sim, siga a skill dna (/dna) e, no fim, acrescente a referência em "Referências relacionadas" da nota: `ref-NNN · Box_de_Ideias/dna/dna_ref-NNN.md · o que ensina`.
7. **Áudio ou vídeo do José.** Ofereça a transcrição. Com o sim, mande uma OS curta ao pilar ideias: MÉTODO dna-do-video (só extração de conteúdo); ENTREGA a transcrição em "A ideia" da nota, abaixo do link, marcada "transcrição automática, pode ter erros". A transcrição local precisa do faster-whisper instalado; pela ElevenLabs, o José autoriza o envio do áudio e o custo.
8. **Confirme** em 1 ou 2 linhas:
   ```
   Guardei: ide-007 «porta que puxa» (nova) em Box_de_Ideias/ideias/2026-10-04_porta-que-puxa.md.
   Quer o DNA do vídeo do link?
   ```

## Status das ideias
| Status | Quando | Quem muda |
|---|---|---|
| nova | o José guardou, ou aprovou uma sugerida | /ideia, orquestrador |
| sugerida | o pilar ideias sugeriu a partir de um DNA; espera o José | pilar ideias |
| em brainstorm | o José está desenvolvendo a ideia, ainda sem projeto; o brainstorm fica em Box_de_Ideias/ideias/<nome-da-nota>_brainstorm_vNN.md | orquestrador |
| em projeto | virou projeto; escreva `em projeto (Projetos/<pasta>/)` | /novo-projeto |
| usada | o vídeo ficou pronto (P6 aprovado), ou a ideia entrou em outro projeto | orquestrador |
| arquivada | o José descartou; a nota fica, nada é apagado | orquestrador |

- Sugerida que o José aprovar vira nova; a que ele descartar vira arquivada.
- Ao mudar o status, atualize junto o frontmatter da nota e a linha do índice.

## Exemplo
José: `/ideia e se o vilão fosse a própria porta? ela escolhe quem entra. curta, tom de suspense`

Nota `Box_de_Ideias/ideias/2026-10-04_porta-vila.md`:
```
---
id: ide-008
data: 2026-10-04
titulo: porta vilã
tipo: curta
tags: [suspense, porta]
status: nova
origem: José (texto)
---
# porta vilã

## A ideia
e se o vilão fosse a própria porta? ela escolhe quem entra. curta, tom de suspense
```
(As outras seções do modelo seguem abaixo, vazias.)

Linha no índice:
```
| ide-008 | 2026-10-04 | porta vilã | curta | suspense, porta | nova | José (texto) | Box_de_Ideias/ideias/2026-10-04_porta-vila.md |
```

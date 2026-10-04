# Box de Ideias

Onde entra tudo que pode virar vídeo: suas ideias (soltas, roteiros, áudios, links) e as referências de terceiros que valem estudo. O pilar 1 (ideias) organiza o Box, faz o DNA dos vídeos de referência e sugere ideias novas a partir deles.

```
Box_de_Ideias/
  indice.md                 o índice de tudo: ideias e referências
  ideias/                   uma nota por ideia: AAAA-MM-DD_<titulo>.md
  referencias/<categoria>/  vídeos de terceiros e o links.md da categoria
    criativos-ads/          anúncios e criativos
  dna/                      os DNAs (dna_ref-NNN.md) e a pasta de trabalho de cada um
```

## Guardar uma ideia
- `/ideia` e o que você tiver: texto, link, áudio ou arquivo.
  Ex.: `/ideia um cara que sempre puxa a porta errada, até o dia em que a porta puxa ele`
- Suas palavras entram na seção "A ideia" como você disse, sem edição. A ideia ganha um id (ide-001) e entra no índice como "nova".
- Pode também soltar arquivos direto em `ideias/` e depois pedir "organize o Box": o pilar ideias cria as notas, classifica e atualiza o índice. O seu arquivo fica intacto.
- Modelo da nota: `_Sistema/templates/ideia.md`.

## Guardar uma referência
- Cada categoria é uma pasta em `referencias/`. Começa com `criativos-ads`; crie outras quando quiser (ex.: virais, historias-ia, clipes).
- Vídeo salvo: `AAAA-MM-DD_<perfil-ou-marca>_<tema>.mp4` na pasta da categoria.
- Só o link: uma linha no `links.md` da categoria: `- data | link | plataforma | por que salvou | métricas`.
- Cada referência ganha um id (ref-001). Detalhes no LEIA-ME de cada categoria.

## DNA do vídeo
- `/dna <link ou arquivo>`. O orquestrador registra a referência e o pilar ideias faz a análise.
- O DNA fica em `dna/dna_ref-NNN.md`: ficha técnica, resumo, os momentos de viralização com força de 1 a 5, gancho, transcrição com tempos, estrutura em batidas, ritmo, texto na tela, áudio, visual, personagens, CTA, métricas, notas por critério, o que aproveitar e de 3 a 5 ideias derivadas.
- As ideias derivadas entram no Box como "sugerida". Diga quais ficam (viram "nova") e quais arquivar.
- O pilar não assiste ao vídeo: ele lê frames com o tempo gravado, a transcrição e o áudio medido. Por isso o DNA separa fato de hipótese.
- Com o arquivo, a análise é completa. Só com o link, sai parcial. Baixar pelo link só com o seu "sim".
- Ferramentas no seu computador: ffmpeg (necessário para o DNA completo); para transcrever, o faster-whisper (local, grátis) ou o ElevenLabs Scribe (pela API, pago, recebe só o áudio); o yt-dlp é opcional. Nada é instalado nem pago sem o seu "sim".

## Status das ideias
| Status | Quando |
|---|---|
| nova | você guardou, ou aprovou uma sugerida |
| sugerida | o pilar ideias sugeriu a partir de um DNA; espera você |
| em brainstorm | você está desenvolvendo a ideia, ainda sem projeto; o brainstorm fica ao lado da nota: `ideias/<nome-da-nota>_brainstorm_vNN.md` |
| em projeto | virou projeto; o índice mostra a pasta: em projeto (Projetos/<pasta>/) |
| usada | o vídeo ficou pronto, ou a ideia entrou em outro projeto |
| arquivada | você descartou; a nota fica, nada é apagado |

## Da ideia ao vídeo
`/novo-projeto` com a ideia (pelo id ou pelo título). O pilar ideias monta a ficha da ideia com os DNAs relacionados, e o projeto segue pelos portões P0 a P6.

## Regras
- Referência é estudo, nunca cópia: aproveitamos princípios, não falas, imagens, personagens, música ou marca.
- Nada é apagado nem movido.
- Ficam fora do git: o `indice.md`, as notas de `ideias/`, os vídeos e os `links.md` de `referencias/` e tudo de `dna/`. Vão para o git só este README e os LEIA-ME. O modelo vazio do índice está em `_Sistema/templates/indice-box.md`.

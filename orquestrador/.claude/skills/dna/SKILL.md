---
name: dna
description: Registra um vídeo de referência (arquivo ou link) no Box de Ideias e pede ao pilar ideias o DNA do vídeo, com os momentos de viralização e as ideias derivadas. Use quando o José digitar /dna ou pedir para analisar um vídeo de referência.
argument-hint: <link ou arquivo> [categoria] [por que salvou]
---
# /dna — DNA de um vídeo de referência

Você registra a referência e delega a análise ao pilar ideias. Não analise o vídeo você mesmo.

## 1. Entrada
- **Arquivo**: o caminho de um vídeo. Ele fica onde o José pôs: não mova, não renomeie, não copie. Se estiver fora do Box, sugira uma vez guardar em Box_de_Ideias/referencias/<categoria>/ com o nome `AAAA-MM-DD_<perfil-ou-marca>_<tema>.mp4`.
- **Link**: TikTok, Reels, Shorts, YouTube, Biblioteca de Anúncios da Meta etc.
- **Categoria**: a que o José disse. Se não disse, a pasta mais provável em Box_de_Ideias/referencias/ (anúncio vai para criativos-ads) e avise qual usou. Categoria nova: crie a pasta (minúsculas, hífen) com um links.md vazio.
- **Por que salvou e métricas**: anote o que o José disse. Não pergunte se ele não trouxe; o DNA marca "sem métrica informada".
- **Já analisada?** Procure o link ou o arquivo no índice. Se já houver DNA, mostre o caminho e pergunte se quer refazer (sai dna_ref-NNN_v02.md).
- Vários vídeos de uma vez: registre todos e mande uma OS por vídeo, um depois do outro (a transcrição local pesa no computador do José).

## 2. Registro
1. **Id**: próximo ref-NNN da tabela Referências de Box_de_Ideias/indice.md (o maior + 1; a primeira é ref-001).
2. **Link**: acrescente 1 linha ao final de Box_de_Ideias/referencias/<categoria>/links.md (crie o arquivo, com a linha `# Links — <categoria>`, se ainda não existir):
   ```
   - AAAA-MM-DD | <link> | <plataforma> | <por que salvou> | <métricas, ou —>
   ```
3. **Índice**, tabela Referências (se Box_de_Ideias/indice.md não existir, crie-o a partir de _Sistema/templates/indice-box.md):
   ```
   | ref-NNN | AAAA-MM-DD | <categoria> | <link ou caminho do arquivo> | a analisar | | |
   ```

## 3. Permissões
Só quando houver link sem arquivo. Baixar a partir do link só com o "sim" do José. Pergunte uma vez (AskUserQuestion), com a recomendação:
- **Você salva o vídeo pelo app** e põe em Box_de_Ideias/referencias/<categoria>/ (recomendado): análise completa, sem risco com os termos da plataforma. Espere o arquivo antes de delegar.
- **yt-dlp só para ler os dados públicos**, sem baixar: DNA parcial (métricas, legenda, música, legenda automática do YouTube), sem frames.
- **yt-dlp para baixar o vídeo**: análise completa; o vídeo fica na pasta da categoria, fora do git.

A resposta vai na linha LIMITES (`yt-dlp não`, `yt-dlp só dados` ou `yt-dlp baixar`).

Transcrição: o padrão é local (faster-whisper), sem custo. O ElevenLabs Scribe é pago e recebe o áudio do vídeo: não pergunte antes. Se o pilar devolver a pendência, pergunte ao José dizendo o serviço, o que vai (só o áudio) e o custo estimado, e retome o mesmo agente com a resposta.

## 4. Ordem de serviço
```
OS box-ref-NNN | ideias
OBJETIVO: DNA do vídeo da referência ref-NNN, com os momentos de viralização e 3 a 5 ideias derivadas
MÉTODO: dna-do-video
ENTRADAS: <caminho do vídeo ou link>; Box_de_Ideias/indice.md; <links.md da categoria, se for link>
ENTREGA: Box_de_Ideias/dna/dna_ref-NNN.md; ideias sugeridas em Box_de_Ideias/ideias/ e no índice
ACEITE: momentos com tempo e força 1-5; fato separado de hipótese; métricas só informadas ou lidas; ideias sem cópia
LIMITES: yt-dlp <não | só dados | baixar> · Scribe <não | sim, até US$ X> · gasto 0 · não instalar nada
```
Descrição curta da chamada do agente: `DNA ref-NNN`.

## 5. Quando o pilar responder
- **concluido**: confira no índice a referência como "analisada", o caminho do DNA e as ideias derivadas como "sugerida". O pilar registra tudo; se faltar alguma linha, acrescente você.
- **parcial ou bloqueado**: leve as PENDENCIAS ao José (perguntas certas, com sugestão) e retome o mesmo agente com a resposta.
- **Falta ferramenta**: mostre ao José o comando de instalação que o pilar sugeriu e só instale depois do "sim".

## 6. Reporte ao José (até 5 linhas)
```
DNA ref-NNN pronto: Box_de_Ideias/dna/dna_ref-NNN.md
O vídeo: <formato e gancho em 1 frase>
Momentos fortes: 00:01 <o quê> (5) · 00:07 <o quê> (4)
Ideias sugeridas: ide-NNN <título> · ide-NNN <título> · ide-NNN <título>
Precisa de você: <quais sugeridas ficar; pendência; ou "nada">
```
As sugeridas que o José aprovar viram "nova"; as que ele descartar viram "arquivada" (nota e índice juntos).

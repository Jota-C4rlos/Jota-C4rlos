---
name: dna-do-video
description: Método do pilar ideias para analisar um vídeo de referência (arquivo ou link) sem assisti-lo - dados técnicos, cortes, frames com tempo, áudio e transcrição com ffmpeg - e montar o DNA do vídeo com os momentos de viralização pontuados. Use em toda OS de DNA e quando for preciso extrair o áudio ou a transcrição de um vídeo.
user-invocable: false
---
# DNA do vídeo

Você não assiste ao vídeo. Você lê os dados do arquivo, os cortes medidos, frames com o tempo gravado na imagem, a curva de volume e a transcrição. Isso é fato. O que você conclui a partir disso (por que prende, que emoção causa) é hipótese e vai marcado.

## Regras
- Referência é estudo: extraia estrutura e princípios (gancho, ritmo, batidas). Nunca copie falas, personagens, imagens, música ou marca.
- Permissões vêm da linha LIMITES da OS: `yt-dlp` (não, só dados ou baixar), `Scribe` (não, ou sim até US$ X) e gasto. O que não estiver autorizado vira pergunta em PENDENCIAS.
- Não instale nada. Faltou ferramenta: PENDENCIAS com o comando da seção Instalação.
- Não apague nada. Não mova nem renomeie o vídeo.
- Métricas: só as que o José informou ou que você leu na página, com a data da leitura. Nunca estime.
- Comentários de terceiros: só os temas, sem @ nem nomes.
- Cite a fonte no DNA: link ou arquivo, perfil, data.

## Pastas
- Vídeo: onde o José deixou; em geral `Box_de_Ideias/referencias/<categoria>/AAAA-MM-DD_<perfil-ou-marca>_<tema>.mp4`.
- Trabalho: `Box_de_Ideias/dna/<ref-id>/` (probe.json, cortes.txt, audio_16k.wav, silencios.txt, loudness.txt, transcricao.json) e `frames/` dentro dela.
- Entrega: `Box_de_Ideias/dna/dna_<ref-id>.md`, pelo modelo [modelo-dna.md](modelo-dna.md) desta pasta. Refazer: `dna_<ref-id>_v02.md`.
- Tudo isso fica fora do git.

## Shell no Windows
- A sua ferramenta Bash é o Git Bash. Os comandos abaixo estão nessa sintaxe e foram testados com FFmpeg 6.1.1 no Linux; o José usa o 9.x no Windows.
- A pasta não se mantém entre chamadas: comece cada chamada com `cd "Box_de_Ideias/dna/<ref-id>" &&`.
- `<video>`: do Box, `"../../referencias/<categoria>/<arquivo>.mp4"`; fora do vault, caminho absoluto com barras normais (`"C:/Users/<usuario>/Videos/<arquivo>.mp4"`).
- Dentro de filtros (`file=`, `fontfile=`), só caminhos relativos.
- Filtro sempre entre aspas duplas, com as aspas simples do ffmpeg dentro: o comando roda igual no Git Bash, no PowerShell e no cmd.
- Se o José rodar à mão no PowerShell: não use `>` para gravar (o PowerShell 5.1 grava em UTF-16); os comandos já gravam com `-o` ou `file=`. grep, cut e awk só existem no Git Bash. Num arquivo .bat, todo `%` vira `%%` (`corte_%%03d.jpg`, `%%{pts\:hms}`, `%%(id)s`).
- Se o Git Bash converter um argumento que começa com `/`, ponha `MSYS_NO_PATHCONV=1` antes do comando.

## 0. Ferramentas
```bash
ffmpeg -version | head -1; ffprobe -version | head -1; yt-dlp --version; py -3.12 --version
py -3.12 -c "import faster_whisper; print('faster-whisper ok')"
[ -n "$ELEVENLABS_API_KEY" ] && echo "ELEVENLABS_API_KEY definida" || echo "ELEVENLABS_API_KEY ausente"
```
Nunca imprima o valor da chave. Sem o Python 3.12, tente `py` ou `python`. Sem ffmpeg não há DNA completo: devolva "bloqueado" com o comando de instalação.

## 1. Fonte
Crie a pasta de trabalho: `mkdir -p "Box_de_Ideias/dna/<ref-id>/frames"`.
- Arquivo: siga para o passo 2.
- Só link, conforme a linha LIMITES:
  - `yt-dlp só dados`: leia os metadados sem baixar (abaixo). DNA parcial, sem frames.
  - `yt-dlp baixar`: baixe para a pasta da categoria e siga com o arquivo.
  - `yt-dlp não`, ou yt-dlp não instalado: DNA parcial com o que a OS e o links.md trazem; em PENDENCIAS, peça que o José salve o vídeo pelo app em `Box_de_Ideias/referencias/<categoria>/`.
- WebFetch em páginas do TikTok e do Instagram costuma falhar (JavaScript, login). Não conte com ele.

```bash
# dados sem baixar (meta.info.json pode ter dados pessoais: fica fora do git)
cd "Box_de_Ideias/dna/<ref-id>" && yt-dlp --skip-download --write-info-json -o "meta" "<link>"
yt-dlp --skip-download --print "%(id)s|%(duration)s|%(view_count)s|%(like_count)s|%(comment_count)s|%(repost_count)s|%(save_count)s|%(track)s|%(upload_date)s" "<link>"
# YouTube e Shorts: legenda automática (transcrição sem baixar) e "Mais repetidos" (retenção por trecho)
cd "Box_de_Ideias/dna/<ref-id>" && yt-dlp --skip-download --write-auto-subs --sub-langs "pt.*" -o "legenda" "<link>"
yt-dlp --skip-download --print "%(heatmap)j" "<link>"
# baixar: só com "yt-dlp baixar" (rode da raiz do vault, sem cd)
yt-dlp -t mp4 -o "Box_de_Ideias/referencias/<categoria>/AAAA-MM-DD_<perfil>_<tema>.%(ext)s" "<link>"
```
- No TikTok, `repost_count` são os compartilhamentos e `save_count` os salvamentos. O yt-dlp não traz os comentários do TikTok.
- O "Mais repetidos" do YouTube é o único sinal público de retenção por trecho (evidência A). Se ele existe para Shorts: a confirmar no primeiro uso.
- Instagram costuma pedir login. Não use cookies do navegador sem o José pedir: peça que ele salve o vídeo.
- Extractors do TikTok e do Instagram quebram com frequência. Falhou: reporte. Atualizar o yt-dlp (`yt-dlp -U`) só com aprovação.

## 2. Dados técnicos
```bash
cd "Box_de_Ideias/dna/<ref-id>" && ffprobe -v error -show_entries "stream=codec_type,codec_name,width,height,r_frame_rate,nb_frames,sample_rate,channels:stream_side_data=rotation:format=duration,bit_rate" -of json -o probe.json "<video>"
```
Leia em probe.json a duração, a largura e a altura (proporção), o fps e se há stream de áudio. Rotação de 90 ou -90: largura e altura estão trocadas.

## 3. Cortes e ritmo
```bash
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -an -vf "select='gt(scene,0.30)',metadata=print:file=cortes.txt" -f null -
cd "Box_de_Ideias/dna/<ref-id>" && grep -o 'pts_time:[0-9.]*' cortes.txt | cut -d: -f2 > cortes_s.txt && awk -v dur=<duracao_em_s> '
{c[NR]=$1}
END{n=NR; printf "cortes: %d | planos: %d | duracao media de plano: %.2f s | cortes por segundo: %.2f\n", n, n+1, dur/(n+1), n/dur
 if(n) printf "primeiro corte: %.2f s\n", c[1]
 a=0; b=0; for(i=1;i<=n;i++){if(c[i]<3)a++; if(c[i]<5)b++}; printf "cortes em 0-3 s: %d | em 0-5 s: %d\n", a, b
 m=0; for(i=1;i<=n;i++){k=0; for(j=i;j<=n&&c[j]<c[i]+5;j++)k++; if(k>m)m=k}; printf "planos em 5 s (max): %d\n", m+1}' cortes_s.txt
```
- Limiar 0.30 (a documentação do ffmpeg indica de 0.3 a 0.5). Talking head com jump cuts: baixe para 0.20 a 0.25. Flash ou câmera rápida gerando corte falso: suba para 0.40. Registre o limiar usado.
- Fusões e transições suaves costumam escapar: confira nas folhas (passo 4).
- Conferência opcional: `ffmpeg -hide_banner -i "<video>" -an -vf "scdet=threshold=10" -f null - 2>&1 | grep -o 'lavfi.scd.time: [0-9.]*'` (bons valores de 8 a 14).

## 4. Frames e folhas de contato
```bash
# gancho: 0 a 3 s, 4 quadros por segundo, numa folha 6x2
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -t 3 -i "<video>" -vf "fps=4,scale=320:-2,drawtext=text='%{pts\:hms}':x=6:y=6:fontsize=24:fontcolor=white:box=1:boxcolor=black@0.6:boxborderw=4,tile=6x2:padding=6:margin=6" -frames:v 1 frames/gancho_0-3s.jpg
# um frame por plano (o primeiro e cada corte), soltos e em folhas 5x4
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -vf "select='eq(n,0)+gt(scene,0.30)',scale=480:-2,drawtext=text='%{pts\:hms}':x=10:y=10:fontsize=36:fontcolor=white:box=1:boxcolor=black@0.6:boxborderw=6" -fps_mode vfr -q:v 3 frames/corte_%03d.jpg
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -vf "select='eq(n,0)+gt(scene,0.30)',scale=320:-2,drawtext=text='%{pts\:hms}':x=6:y=6:fontsize=24:fontcolor=white:box=1:boxcolor=black@0.6:boxborderw=4,tile=5x4:padding=6:margin=6" -fps_mode vfr -q:v 3 frames/cortes_%02d.jpg
# o vídeo todo, 2 quadros por segundo (fps=1 acima de 90 s), 20 por folha
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -vf "fps=2,scale=320:-2,drawtext=text='%{pts\:hms}':x=6:y=6:fontsize=24:fontcolor=white:box=1:boxcolor=black@0.6:boxborderw=4,tile=5x4:padding=6:margin=6" -fps_mode vfr -q:v 3 frames/folha_%02d.jpg
# um quadro exato, quando um momento importar (o tempo vai no nome)
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -ss 00:00:01.250 -i "<video>" -frames:v 1 -q:v 3 frames/quadro_00-01-250.jpg
```
- Use nos frames o mesmo limiar de corte do passo 3.
- O tempo gravado na imagem sai como HH:MM:SS.mmm.
- Uma folha 5x4 de vídeo 9:16 sai com 1636x2302 px, abaixo do limite de cerca de 2576 px no lado maior que o Claude lê sem reduzir (limite a confirmar).
- Erro de fonte no drawtext (build sem fontconfig): ponha `fontfile='C\:/Windows/Fonts/arial.ttf':` logo depois de `drawtext=` (a confirmar no Windows).

## 5. Áudio
Sem stream de áudio no probe.json, pule os passos 5 e 6.
```bash
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -vn -ac 1 -ar 16000 -c:a pcm_s16le audio_16k.wav
# silêncios (pausa, respiro antes do drop)
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -vn -af "silencedetect=noise=-35dB:d=0.3,ametadata=mode=print:file=silencios.txt" -f null - && grep -o 'silence_[a-z]*=[0-9.]*' silencios.txt
# volume a cada 100 ms, resumido no máximo de cada segundo (LUFS)
cd "Box_de_Ideias/dna/<ref-id>" && ffmpeg -hide_banner -loglevel error -i "<video>" -vn -af "ebur128=metadata=1,ametadata=mode=print:key=lavfi.r128.M:file=loudness.txt" -f null - && awk -F'[ =:]+' '/pts_time/{t=$NF} /r128.M/{s=int(t); v=$NF; if(!(s in m)||v>m[s]) m[s]=v} END{for(s in m) printf "%d %.1f\n", s, m[s]}' loudness.txt | sort -n
```
- Pico: segundo bem acima dos vizinhos (drop, efeito, grito). Queda: silêncio ou vale antes de um pico (tensão). Cruze com os cortes.
- Os primeiros 400 ms aparecem como -120: é a janela da medição, não silêncio.
- Música o tempo todo quase não deixa silêncio: use a curva de volume.

## 6. Transcrição
Ordem: (a) local, se o faster-whisper estiver instalado; (b) ElevenLabs Scribe v2, se a variável `ELEVENLABS_API_KEY` existir e a OS disser `Scribe sim`; (c) legenda automática do YouTube (passo 1); (d) nenhuma: PENDENCIAS com as opções (instalar o faster-whisper, autorizar o Scribe ou o José colar as falas).

(a) Local, sem custo. Na primeira vez, o modelo é baixado da internet (uma vez só).
```bash
cd "Box_de_Ideias/dna/<ref-id>" && PYTHONUTF8=1 py -3.12 - audio_16k.wav transcricao.json pt <<'EOF'
import json, sys
from faster_whisper import WhisperModel
wav, saida, idioma = sys.argv[1], sys.argv[2], sys.argv[3]
modelo = WhisperModel("turbo", device="cpu", compute_type="int8")
segs, info = modelo.transcribe(wav, language=None if idioma == "auto" else idioma,
                               word_timestamps=True, vad_filter=True, beam_size=5)
res = []
for s in segs:
    palavras = [{"p": w.word.strip(), "ini": round(w.start, 2), "fim": round(w.end, 2)} for w in (s.words or [])]
    res.append({"ini": round(s.start, 2), "fim": round(s.end, 2), "texto": s.text.strip(), "palavras": palavras})
    print(f"[{s.start:06.2f}-{s.end:06.2f}] {s.text.strip()}")
with open(saida, "w", encoding="utf-8") as f:
    json.dump({"idioma": info.language, "segmentos": res}, f, ensure_ascii=False, indent=1)
EOF
```
- Idioma: `pt`, `en`, `es`... ou `auto`. Lento demais? Troque `"turbo"` por `"small"`. Não use os modelos distil-* para português.
- Letra cantada: rode também com `vad_filter=False` e compare; o Whisper erra mais em música.

(b) Scribe v2 pela API: pago, envia só o áudio à ElevenLabs. Preço citado: US$ 0,22 por hora de áudio, ou seja, menos de 1 centavo de dólar por minuto (a confirmar na página de preços). Informe o gasto em CUSTO.
```bash
cd "Box_de_Ideias/dna/<ref-id>" && curl -sS -X POST "https://api.elevenlabs.io/v1/speech-to-text" -H "xi-api-key: $ELEVENLABS_API_KEY" -F model_id=scribe_v2 -F timestamps_granularity=word -F diarize=true -F tag_audio_events=true -F file=@audio_16k.wav -o transcricao_scribe.json
```
- `model_id`, `timestamps_granularity`, `diarize` e `tag_audio_events` são da documentação oficial. O endereço da API é a confirmar no primeiro uso, na documentação (Fontes).
- Com o CLI oficial instalado: `elevenlabs speech-to-text convert --file audio_16k.wav --model-id scribe_v2`.
- Em `words`, o tipo `audio_event` marca risadas e aplausos: é sinal de momento forte (evidência B).

No DNA, uma linha por fala: `[00:01.2–00:03.4] texto`. Tire daí o tempo até a primeira palavra, as palavras por segundo, o % do tempo com fala e a frase literal do gancho.

## 7. Olhar os frames
Leia com a ferramenta Read, nesta ordem: `gancho_0-3s.jpg`, `cortes_NN.jpg`, as `folha_NN.jpg` necessárias e os `quadro_*.jpg` que gerar.
- Cite sempre o tempo gravado no frame.
- O texto na tela sai dos frames; texto que entra e sai entre duas amostras pode escapar.
- Movimento (zoom, pan, gesto) você só deduz pela diferença entre frames: é hipótese.
- Momento importante entre duas amostras: gere um quadro exato em vez de supor.

## 8. Montar o DNA
Siga o [modelo-dna.md](modelo-dna.md) e preencha todas as seções, nesta ordem de trabalho (no arquivo, os momentos e o gancho vêm logo depois do resumo, para o José ler primeiro o que pediu).
1. Ficha técnica com os números dos passos 2, 3, 5 e 6. Campo sem dado fica "—".
2. Batidas: uma linha por plano; junte planos muito curtos com a mesma função.
3. Momentos de viralização: cruze os sinais no mesmo tempo (corte, pico de volume, silêncio antes de pico, frase-chave, texto novo, evento sonoro, pico no "Mais repetidos", comentário que cita o momento). Dois sinais ou mais no mesmo segundo: candidato forte. De 3 a 7 momentos, cada um com força 1-5 e evidência A, B ou C.
4. Gancho: as 4 camadas dos 3 primeiros segundos (imagem, fala, texto, som), o tipo e a força.
5. Notas por critério: as marcas ABCD (sim ou não, com o tempo) e as notas de 1 a 5 com justificativa.
6. O que aproveitar: princípios, cada um com a tradução para o nosso fluxo (pilar e como). E o que não copiar.
7. Ideias derivadas: de 3 a 5, como manda o agente (notas "sugerida" e linhas no índice).
8. Limitações desta análise.

## 9. Fechar
- Índice: referência "analisada", caminho do DNA e ids das ideias derivadas.
- Nada é apagado. Se baixou o vídeo, diga no RESUMO onde ele está: o José decide o que fazer com ele.
- CUSTO: o gasto do Scribe, ou 0.

## Só extração de conteúdo
OS que pede só o áudio ou a transcrição (de uma referência ou de um áudio do José): passos 0, 2, 5 e 6, com a pasta de trabalho `Box_de_Ideias/dna/<id>/` (id da referência ou da ideia). Aula de curso: pasta de trabalho e entrega em `_Sistema/academia/material/<tema>/transcricoes/` (fora do git), com o nome do arquivo da aula. Entregue no caminho da OS uma linha por fala, `[00:01.2–00:03.4] texto`, marcada "transcrição automática, pode ter erros".

## Instalação (só com o "sim" do José)
| Ferramenta | Comando | Versão em 2026-10-04 |
|---|---|---|
| ffmpeg e ffprobe | `winget install --id Gyan.FFmpeg -e` | 9.0.2 (20/09/2026) |
| yt-dlp | `winget install --id yt-dlp.yt-dlp -e` (traz o Deno e um ffmpeg próprio) | 2026.08.19 |
| Python | `winget install --id Python.Python.3.12 -e` | 3.12.10 |
| faster-whisper | `py -3.12 -m pip install -U faster-whisper` | 1.2.1 (31/10/2025) |
| PySceneDetect (opcional) | `py -3.12 -m pip install -U scenedetect opencv-python` | 0.7.1 (22/07/2026) |
| CLI da ElevenLabs (opcional) | `scoop install elevenlabs` ou `npm i -g @elevenlabs/cli` | — |

Depois de instalar, pode ser preciso reabrir o Claude Code para o PATH atualizar. Conferir: passo 0.

## Fontes
- FFmpeg, filtros (select/scene, scdet, tile, drawtext, silencedetect, ebur128): https://github.com/FFmpeg/FFmpeg/blob/master/doc/filters.texi e ffprobe: https://github.com/FFmpeg/FFmpeg/blob/master/doc/ffprobe.texi (master em 2026-10-04; comandos testados com FFmpeg 6.1.1).
- FFmpeg no winget: https://github.com/microsoft/winget-pkgs/tree/master/manifests/g/Gyan/FFmpeg/9.0.2 (2026-09-20).
- Claude Code no Windows (Git Bash e PowerShell): https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md (v2.1.289, 2026-10).
- yt-dlp: https://github.com/yt-dlp/yt-dlp (2026-08-19); sites e extractors: https://github.com/yt-dlp/yt-dlp/blob/master/supportedsites.md e https://github.com/yt-dlp/yt-dlp/blob/master/yt_dlp/extractor/tiktok.py (2026-10-04).
- faster-whisper: https://github.com/SYSTRAN/faster-whisper (README em 2026-10-04; PyPI 1.2.1 de 2025-10-31).
- PySceneDetect: https://github.com/Breakthrough/PySceneDetect (0.7.1, 2026-07-22).
- Python e wheels no Windows: https://pypi.org/project/ctranslate2/ (2026-08 a 2026-10).
- ElevenLabs Scribe v2: https://github.com/elevenlabs/skills/tree/main/speech-to-text (2026-10-01); https://elevenlabs.io/blog/introducing-scribe-v2 (2026-01); API: https://elevenlabs.io/docs/api-reference/speech-to-text/convert (2026); preço: https://elevenlabs.io/pricing/api (2026, a confirmar).
- Leitura de imagens em alta resolução: skill claude-api embutida no Claude Code, shared/model-migration.md (2026-09-25; a confirmar).
- Critérios ABCD: fontes no fim do modelo-dna.md.

Se a ferramenta mudou, peça ao pilar skills a atualização.

# Formato do status.md

O painel de agentes e a rede leem o status.md de cada projeto. Siga este formato à risca.

## Cabeçalho
Uma `chave: valor` por linha.
- `projeto`: nome curto. `cliente`: o nome do cliente, ou `proprio`.
- `resumo`: uma linha sobre o projeto (ex.: Curta por IA · 60 s · 9:16 · hiper-realista).
- `ideia`: o caminho da ideia no Box (ex.: Box_de_Ideias/ideias/2026-09-28_porta-errada.md), ou `nova`.
- `formato`: proporção e duração (ex.: 9:16 · 60 s).
- `metodo_roteiro`, `estetica`, `modelo_imagem`, `modelo_video`, `modelo_musica`: as escolhas do José, com o nome da skill ou da ferramenta (ex.: roteiro-padrao, hiper-realista, Midjourney, Seedance, Suno). Vazio até a escolha.
- `etapa`: intake, brainstorm, roteiro, visual, prompts, geração, música ou retrospectiva. Com a música em paralelo, vale a etapa principal.
- `portao`: o primeiro portão ainda não aprovado, como `P4 pendente`; no fim do projeto, `P6 aprovado`.
- `prazo_entrega`: `AAAA-MM-DD`, ou vazio.

## Tabelas e listas
- Aprovações: uma linha por decisão. Data em `AAAA-MM-DD HH:MM`. Decisão: `aprovado`, `ajustes` ou `reprovado`.
- Tarefas: status `a fazer`, `em andamento`, `entregue` ou `bloqueado`. Coluna Entrega: o caminho do arquivo entregue; em tarefa bloqueada, o motivo em poucas palavras.
- Takes: uma linha por take, criada quando o P4 for aprovado. Take: `take-01`. Prompt: a versão em uso (`v01`). Tentativas: quantas gerações o José fez. Status: `a gerar`, `gerado`, `ajuste` ou `aprovado`. Arquivo: o caminho do take escolhido, ou vazio.
- Pendência com o José, uma por linha: `- portão | agente | o que decidir | arquivo | detalhe`. O detalhe é opcional; sem portão ou sem agente, use `—`.
- Pendência com o cliente, uma por linha: `- o que falta | pedido em AAAA-MM-DD`.
- Datas em `AAAA-MM-DD`. Caminhos relativos à pasta do projeto. Os textos não usam `|`.

## Exemplo de linhas preenchidas

| Portão | Data | Decisão | Observação |
|---|---|---|---|
| P3 | 2026-10-02 14:12 | aprovado | estética hiper-realista |

| # | Agente | Tarefa | Status | Entrega |
|---|---|---|---|---|
| 6 | prompts | Takes v1 | entregue | 04_Prompts/takes_v01.md |
| 7 | musica | Música v1 | em andamento | |

| Take | Prompt | Tentativas | Status | Arquivo |
|---|---|---|---|---|
| take-01 | v01 | 2 | aprovado | 05_Geracao/takes/take-01_t02.mp4 |
| take-02 | v02 | 1 | ajuste | |

- P4 | prompts | Aprovar os prompts dos takes | 04_Prompts/takes_v01.md | 6 takes · Seedance · 9:16
- Logo do cliente em vetor | pedido em 2026-10-02

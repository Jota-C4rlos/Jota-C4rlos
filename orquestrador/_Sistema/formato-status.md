# Formato do status.md

O painel de agentes e a rede (a instalar) vão ler o status.md de cada projeto. Siga este formato à risca.

- Cabeçalho: uma `chave: valor` por linha.
- `resumo`: uma linha sobre o projeto (ex.: Roteiro de vídeo · 30 s · 9:16).
- `etapa`: intake, conceito ou roteiro. As próximas etapas entram com os novos pilares.
- `portao`: o primeiro portão ainda não aprovado, como `P2 pendente`; com o roteiro aprovado, `P2 aprovado`.
- Aprovações: uma linha por decisão. Data em `AAAA-MM-DD HH:MM`. Decisão: `aprovado`, `ajustes` ou `reprovado`.
- Tarefas: status `a fazer`, `em andamento`, `entregue` ou `bloqueado`. Coluna Entrega: o caminho do arquivo entregue; em tarefa bloqueada, o motivo em poucas palavras.
- Pendência com o José, uma por linha: `- portão | agente | o que decidir | arquivo | detalhe`. O detalhe é opcional; sem portão ou sem agente, use `—`.
- Pendência com o cliente, uma por linha: `- o que falta | pedido em AAAA-MM-DD`.
- Datas em `AAAA-MM-DD`. Caminhos relativos à pasta do projeto. Os textos não usam `|`.

Exemplo de linhas preenchidas:

| Portão | Data | Decisão | Observação |
|---|---|---|---|
| P1 | 2026-10-02 14:12 | aprovado | caminho 2 |

| # | Agente | Tarefa | Status | Entrega |
|---|---|---|---|---|
| 1 | escrita | Conceitos v1 | entregue | 01_Roteiro/conceitos_v01.md |
| 2 | escrita | Roteiro e decupagem v1 | em andamento | |

- P2 | escrita | Aprovar o roteiro e a decupagem | 01_Roteiro/roteiro_v01.md | 30 s · 6 cenas
- Logo do cliente em vetor | pedido em 2026-10-02

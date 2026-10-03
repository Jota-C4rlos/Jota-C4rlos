# Parte 2 — Painel de agentes do Orquestrador (nativo no Claude Code)

> **Pendente — adaptar antes de instalar.** Este documento veio do kit original e ainda descreve os 7 agentes de lá (writer, form, stock, code, visual, delivery, skill), os portões P3 a P6 e os campos de geração por IA. Quando os 7 pilares do Orquestrador estiverem definidos, troque nomes, funções e dados de demonstração pelos novos. A geometria, as cores por posição e as regras de comportamento continuam valendo.

Você vai construir o painel de agentes do Orquestrador: um painel nativo do Claude Code (um plugin de hooks que desenha um pane ao lado da conversa) que mostra, em tempo real, o projeto atual, o que precisa de mim, os 7 agentes, os portões, as tarefas e o registro. Eu sou o José, único aprovador. O conceito visual já foi aprovado por mim; este prompt traz a especificação e os desenhos de referência.

## Regras desta tarefa

- Isto é instalação do sistema, não projeto de cliente: faça você mesmo, sem delegar aos agentes.
- Não construa nada sem o meu "aprovado" em cada etapa. Comigo, seja conciso, em português, com recomendação clara.
- Antes de escrever qualquer arquivo, carregue a skill `plugin-authoring` do Claude Code. O arquivo de tipos da sua versão é a autoridade. O que este prompt diz sobre a API é um mapa; se divergir dos tipos, valem os tipos, e você me avisa.
- O painel só observa e não custa tokens: não chama o modelo, não escreve na conversa, não usa rede, não roda processos e não escreve no vault.
- A pergunta "Enable hot reloading for this session?", que aparece quando você grava o primeiro arquivo do plugin, é para mim: eu respondo.

## Lições da primeira instalação

- O Svg com animação (`isInteractive`) saiu num quadro de 300 × 150 px, com faixas brancas, por não receber medidas. Passe `width` e `height` explícitos no desenho dos agentes (400 × 280 no layout estreito, 560 × 392 no largo) e garanta que o fundo do quadro nunca apareça branco. Se mesmo assim o quadro ficar em 300 × 150, desenhe sem `isInteractive`: o tamanho certo vale mais que a animação.
- O app não aceitou link `file:` num botão, só em texto formatado. "Abrir o arquivo" vira link, com um botão "copiar o caminho" ao lado.
- A primeira instalação parou no visual de demonstração, sem dados reais, e o plugin ficou numa pasta de sessão que não carrega em sessões novas. Esta parte só termina com a Etapa 2 (dados reais) e a Etapa 3 (pasta definitiva) concluídas.

## Etapa 0 — Verificação (somente leitura)

1. A Parte 1 está instalada? Confira CLAUDE.md, os 7 agentes em .claude\agents (writer, form, stock, code, visual, delivery, skill), _Sistema\templates\status.md e a pasta Projetos\. Se faltar algo, pare e me diga.
2. Sua versão do Claude Code tem a skill `plugin-authoring`, e os tipos dela trazem o pane e o elemento Svg na superfície desktop? Os comandos `claude plugin validate` e `claude plugin test` rodam na minha máquina? Diga a versão: a rota deste prompt foi verificada com um protótipo na 2.1.287, nesses dois comandos, mas ainda não foi vista no app desktop. Se algo faltar, pare e me explique; o plano B é uma página local.
3. Veja como um plugin de hooks fica carregado de forma permanente nas sessões do app desktop abertas na pasta do vault e o que a sua versão exige para isso, inclusive se os hooks de função vêm desligados. Minha preferência: dentro do vault, em .claude\skills\painel, para valer só nas sessões desta pasta e sem mexer em configuração fora dela. A alternativa é a variável CLAUDE_CODE_PLUGIN_DIRS em ~/.claude/settings.json.
4. Me apresente um plano em até 15 linhas: onde o plugin fica durante a construção e depois de instalado, como será carregado, quais eventos e arquivos vai usar. Espere meu "aprovado".

## Etapa 1 — Visual com dados de demonstração

Construa o painel com o comando `/painel demo`, que mostra os dados da seção "Dados de demonstração". O objetivo é reproduzir o conceito aprovado. Valide com `claude plugin validate`, abra o painel e me peça para olhar. Se o pane não aparecer no app desktop, pare e me diga. Espere meu "aprovado" do visual.

## Etapa 2 — Dados reais

Ligue o painel aos eventos da sessão e aos arquivos do vault (seção "De onde vêm os dados"). O formato do status.md já foi instalado na Parte 1 (`_Sistema/formato-status.md`). Se ainda não houver projeto em Projetos\, teste com um status.md de exemplo na pasta de testes do plugin; não crie projeto falso no vault.

## Etapa 3 — Testes e instalação permanente

1. Escreva testes com `claude plugin test` para as superfícies terminal e desktop: agente iniciando e terminando com cada STATUS, leitura de um status.md de exemplo, painel sem projeto e a garantia de que os hooks devolvem o resultado sem alterar nada.
2. Instale o plugin de forma permanente para as sessões abertas na pasta do vault. Se isso mexer em alguma configuração fora do vault, me diga exatamente o quê e peça aprovação antes.
3. Me entregue um resumo em até 10 linhas: onde o plugin ficou, os comandos, como trocar de projeto, como desligar e o que testar no primeiro projeto real.

---

## Especificação

### Blocos, nesta ordem

Rótulos em inglês e caixa alta; conteúdo em português. Fora dos SVGs, o texto usa a fonte do próprio app. O painel é escuro seja qual for o tema do app: fundo `#161616` no elemento raiz e texto `#f4f3f2`. Cantos sempre retos.

1. **Cabeçalho**: `ORQUESTRADOR · AGENTS` à esquerda; à direita, `● LIVE` quando há agente trabalhando e `○ LIVE` quando não há.
2. **Projeto**: título `cliente · projeto`, uma linha de resumo e três campos. `STAGE`: a etapa. `NEXT`: o primeiro portão ainda não aprovado, com o nome curto (`P4 · orçamento`). `DUE`: a data e os dias úteis que faltam (`14/10 · 7 dias úteis`); no dia do prazo, "vence hoje"; depois dele, "atrasado N dias"; sem prazo, "sem prazo".
3. **NEEDS YOU**: o rótulo com a contagem (`NEEDS YOU · 1`) e um cartão com fundo `#303030`. Para cada pendência: o que decidir (negrito), uma linha com o portão e o detalhe (`Portão P4 · 12 cenas · faixa de US$ 40 a 60`), o caminho do arquivo e um botão "Abrir o arquivo" (link `file:`; se o app não abrir, o botão copia o caminho). Abaixo, `WAITING ON CLIENT` com o que falta do cliente. Sem pendências, o cartão vira uma linha: "Nada pendente."
4. **AGENTS**: ao lado do rótulo, o resumo dos estados que têm pelo menos um agente (`2 entregues · 1 ativo · 1 espera · 3 livres`, mais `N bloqueados` quando houver). Abaixo, um único SVG com o prisma, os raios, os dots e as linhas dos 7 agentes (seção "Desenho dos agentes").
5. **GATES**: "N de 7 aprovados" e um SVG com 7 paralelogramos, P0 a P6.
6. **TASKS**: "N de M" (entregues sobre o total) e até 5 linhas, na ordem da tabela: as tarefas em andamento ou bloqueadas, com as entregues mais recentes acima e a próxima a fazer abaixo. Cada linha: marca de estado (✓ entregue, ● em andamento, ○ a fazer, ✕ bloqueada), um quadradinho na cor do agente, o agente e a tarefa. A tarefa em andamento fica em negrito. Um botão "Ver as M tarefas" expande a lista.
7. **LOG**: as 4 últimas ocorrências (entregas, bloqueios, aprovações e recados do mural), com a hora (HH:MM) quando são de hoje e a data (DD/MM) quando não.
8. **BUDGET** e **ACADEMY**: `BUDGET` mostra o gasto de geração sobre o orçamento aprovado e o modo de geração (`US$ 12 de 60 · geração em modo manual`); sem orçamento aprovado, "a aprovar no P4"; a partir de 80% do orçamento, a linha fica em negrito com "limite de 80% atingido". `ACADEMY` mostra quantos cursos estão abertos e, de cada um, `agente · tema`.

Dias úteis: do dia seguinte até o dia do prazo, de segunda a sexta, sem os feriados nacionais (1/1, 21/4, 1/5, 7/9, 12/10, 2/11, 15/11, 20/11, 25/12 e a Sexta-feira Santa).

Nomes curtos dos portões: P0 viabilidade, P1 conceito, P2 roteiro, P3 direção, P4 orçamento, P5 corte, P6 entrega.

Com o corpo do pane largo (cerca de 110 colunas ou mais), use duas colunas: Projeto no topo, com `BUDGET` como quarto campo; à esquerda AGENTS (SVG maior), GATES e ACADEMY; à direita NEEDS YOU, TASKS e LOG. Estreito, empilhe na ordem acima. Ao abrir, peça uma largura em que o desenho de 400 px apareça em tamanho real.

Na superfície de terminal não existe Svg: mostre AGENTS como 7 linhas de texto (● ou ○ na cor do agente, nome, estado, detalhe) e GATES como texto.

### Cores (tema escuro)

| Uso | Cor |
|---|---|
| Fundo | `#161616` |
| Superfície elevada (cartão, prisma) | `#303030` |
| Texto e feixe do orquestrador | `#f4f3f2` |
| Texto secundário | `#f4f3f2` a 70% |
| Fios e separadores | `#f4f3f2` a 12% e 25% |
| writer | `#e6464b` |
| form | `#d4702f` |
| stock | `#fad305` |
| code | `#308f2f` |
| visual | `#5285b7` |
| delivery | `#7471f2` |
| skill | `#c936f6` |

São as cores do espectro, uma por posição (do pilar 1 ao 7), com o vermelho, o anil e o violeta clareados para ter contraste no fundo escuro: use estes valores. Os nomes de cor da tabela de agentes do CLAUDE.md são os que o Claude Code aceita para subagentes; no painel valem os valores acima.

As cores do espectro só aparecem nos raios, nos dots e nos quadradinhos das tarefas. Texto nunca usa cor de agente. Nada de degradê arco-íris nem de cantos arredondados: o canto do sistema é o chanfro de 60°.

### Estados do agente

| Estado | Fio | Dot | 1ª linha | 2ª linha |
|---|---|---|---|---|
| livre | 1,25 px, a 50% | anel vazado, raio 6, traço 2 a 80% | nome e "livre" a 70% | nenhuma |
| trabalhando | 3 px, tracejado `7 5` em movimento (0,9 s) | cheio, raio 7 | "trabalhando" em negrito; hora de início à direita | a tarefa |
| espera você | 2,5 px, cheio | cheio, raio 7, com anel branco de raio 11 pulsando (1,6 s) | "espera você" em negrito; selo do portão à direita | o arquivo que espera a decisão |
| entregue | 2,5 px, cheio | cheio, raio 7 | "entregue" a 70%; hora da entrega à direita | o arquivo entregue |
| bloqueado | 2,5 px, pontilhado `2 5`, parado | anel branco vazado, raio 6, traço 2 | "bloqueado" em negrito; hora à direita | o motivo |

A hora à direita só aparece quando o fato é desta sessão. No layout largo, o agente livre que tem tarefa a fazer mostra "próxima: <tarefa>" na 2ª linha. O estado nunca depende só da cor.

### Desenho dos agentes (referência aprovada)

Use este SVG como molde. A geometria é fixa; mudam os estados, os textos e o selo. `viewBox` 400 × 280, escalando para a largura do painel. Passe `isInteractive` para as animações rodarem.

- Ordem das linhas, de cima para baixo: writer, form, stock, code, visual, delivery, skill. Centro da linha `i` (de 0 a 6): `y = 20 + 40·i`.
- Cada raio sai de um ponto fixo do prisma e chega em `(134, y)`: `(64.63,118)`, `(67.52,123)`, `(70.40,128)`, `(73.29,133)`, `(76.18,138)`, `(79.06,143)`, `(81.95,148)`. O dot fica em `(142, y)`.
- Linha com 2ª linha: bases em `y − 3,5` e `y + 11`. Linha sem 2ª linha: base em `y + 4,5`.
- Nome em `x = 160` (monoespaçada, 13, negrito). Estado em `x = 236` (13). À direita, terminando em `x = 396`: a hora (monoespaçada, 11, a 70%) ou o selo do portão. 2ª linha em `x = 160` (11, a 70%), cortada com "…" em 38 caracteres; de um arquivo, só o nome, sem a pasta.
- Selo do portão: polígono `(370, y−15,5) (392, y−15,5) (396, y−8,57) (396, y+0,5) (370, y+0,5)`, com o texto centrado em `x = 383`, base em `y − 3,5`.
- As listas de fontes pedem primeiro Mulish e JetBrains Mono, se estiverem instaladas no Windows, e caem nas do sistema. Mantenha as listas como estão.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 280" width="400" height="280" font-family="'Mulish', 'Segoe UI', system-ui, sans-serif" role="img" aria-label="Agentes: writer e form entregaram, stock trabalhando, code espera você, visual, delivery e skill livres.">
  <rect width="400" height="280" fill="#161616"/>
  <text x="0" y="127" font-family="'JetBrains Mono', Consolas, ui-monospace, monospace" font-size="9" letter-spacing="0.6" fill="#f4f3f2">CLAUDE</text>
  <line x1="0" y1="140" x2="34.67" y2="140" stroke="#f4f3f2" stroke-width="2.5"/>
  <polygon points="56,103.05 24,158.48 88,158.48" fill="#303030" stroke="#f4f3f2" stroke-width="1.5"/>
  <line x1="34.67" y1="140" x2="73.29" y2="133" stroke="#f4f3f2" stroke-opacity="0.4"/>
  <line x1="64.63" y1="118" x2="134" y2="20" stroke="#e6464b" stroke-width="2.5"/>
  <line x1="67.52" y1="123" x2="134" y2="60" stroke="#d4702f" stroke-width="2.5"/>
  <line x1="70.40" y1="128" x2="134" y2="100" stroke="#fad305" stroke-width="3" stroke-dasharray="7 5"><animate attributeName="stroke-dashoffset" from="0" to="-12" dur="0.9s" repeatCount="indefinite"/></line>
  <line x1="73.29" y1="133" x2="134" y2="140" stroke="#308f2f" stroke-width="2.5"/>
  <line x1="76.18" y1="138" x2="134" y2="180" stroke="#5285b7" stroke-width="1.25" stroke-opacity="0.5"/>
  <line x1="79.06" y1="143" x2="134" y2="220" stroke="#7471f2" stroke-width="1.25" stroke-opacity="0.5"/>
  <line x1="81.95" y1="148" x2="134" y2="260" stroke="#c936f6" stroke-width="1.25" stroke-opacity="0.5"/>
  <circle cx="142" cy="20" r="7" fill="#e6464b"/>
  <circle cx="142" cy="60" r="7" fill="#d4702f"/>
  <circle cx="142" cy="100" r="7" fill="#fad305"/>
  <circle cx="142" cy="140" r="7" fill="#308f2f"/>
  <circle cx="142" cy="140" r="11" fill="none" stroke="#f4f3f2" stroke-width="1.5"><animate attributeName="opacity" values="1;0.25;1" dur="1.6s" repeatCount="indefinite"/></circle>
  <circle cx="142" cy="180" r="6" fill="#161616" stroke="#5285b7" stroke-opacity="0.8" stroke-width="2"/>
  <circle cx="142" cy="220" r="6" fill="#161616" stroke="#7471f2" stroke-opacity="0.8" stroke-width="2"/>
  <circle cx="142" cy="260" r="6" fill="#161616" stroke="#c936f6" stroke-opacity="0.8" stroke-width="2"/>
  <g stroke="#f4f3f2" stroke-opacity="0.12">
    <line x1="160" y1="40" x2="400" y2="40"/><line x1="160" y1="80" x2="400" y2="80"/><line x1="160" y1="120" x2="400" y2="120"/>
    <line x1="160" y1="160" x2="400" y2="160"/><line x1="160" y1="200" x2="400" y2="200"/><line x1="160" y1="240" x2="400" y2="240"/>
  </g>
  <g font-family="'JetBrains Mono', Consolas, ui-monospace, monospace" font-size="13" font-weight="700" fill="#f4f3f2">
    <text x="160" y="16.5">writer</text>
    <text x="160" y="56.5">form</text>
    <text x="160" y="96.5">stock</text>
    <text x="160" y="136.5">code</text>
    <text x="160" y="184.5" fill-opacity="0.7">visual</text>
    <text x="160" y="224.5" fill-opacity="0.7">delivery</text>
    <text x="160" y="264.5" fill-opacity="0.7">skill</text>
  </g>
  <g font-size="13" fill="#f4f3f2">
    <text x="236" y="16.5" fill-opacity="0.7">entregue</text>
    <text x="236" y="56.5" fill-opacity="0.7">entregue</text>
    <text x="236" y="96.5" font-weight="700">trabalhando</text>
    <text x="236" y="136.5" font-weight="700">espera você</text>
    <text x="236" y="184.5" fill-opacity="0.7">livre</text>
    <text x="236" y="224.5" fill-opacity="0.7">livre</text>
    <text x="236" y="264.5" fill-opacity="0.7">livre</text>
  </g>
  <g font-size="11" fill="#f4f3f2" fill-opacity="0.7">
    <text x="160" y="31">roteiro_v02.md</text>
    <text x="160" y="71">direcao-campanha_v01.md</text>
    <text x="160" y="111">inventário e lista de assets</text>
    <text x="160" y="151">plano-geracao_v01.md</text>
  </g>
  <g font-family="'JetBrains Mono', Consolas, ui-monospace, monospace" font-size="11" fill="#f4f3f2" fill-opacity="0.7" text-anchor="end">
    <text x="396" y="16.5">11:20</text>
    <text x="396" y="56.5">13:58</text>
    <text x="396" y="96.5">14:28</text>
  </g>
  <polygon points="370,124.5 392,124.5 396,131.43 396,140.5 370,140.5" fill="#f4f3f2"/>
  <text x="383" y="136.5" font-family="'JetBrains Mono', Consolas, ui-monospace, monospace" font-size="11" font-weight="700" text-anchor="middle" fill="#161616">P4</text>
</svg>
```

### Desenho dos portões (referência aprovada)

Aprovado: paralelogramo cheio claro com texto escuro. Atual (o primeiro ainda não aprovado): contorno claro de 1,75 px com texto claro em negrito. Futuro: contorno a 25% com texto a 70%. Os lados inclinam a 60°.

```svg
<svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 400 28" width="400" height="28" font-family="'JetBrains Mono', Consolas, ui-monospace, monospace" font-size="11" text-anchor="middle" role="img" aria-label="Portões: P0 a P3 aprovados, P4 aguardando você, P5 e P6 a seguir.">
  <rect width="400" height="28" fill="#161616"/>
  <polygon points="15.86,2 54,2 40.14,26 2,26" fill="#f4f3f2"/>
  <polygon points="72.86,2 111,2 97.14,26 59,26" fill="#f4f3f2"/>
  <polygon points="129.86,2 168,2 154.14,26 116,26" fill="#f4f3f2"/>
  <polygon points="186.86,2 225,2 211.14,26 173,26" fill="#f4f3f2"/>
  <polygon points="243.86,2 282,2 268.14,26 230,26" fill="#161616" stroke="#f4f3f2" stroke-width="1.75"/>
  <polygon points="300.86,2 339,2 325.14,26 287,26" fill="none" stroke="#f4f3f2" stroke-opacity="0.25"/>
  <polygon points="357.86,2 396,2 382.14,26 344,26" fill="none" stroke="#f4f3f2" stroke-opacity="0.25"/>
  <g font-weight="700" fill="#161616"><text x="28" y="18">P0</text><text x="85" y="18">P1</text><text x="142" y="18">P2</text><text x="199" y="18">P3</text></g>
  <text x="256" y="18" font-weight="700" fill="#f4f3f2">P4</text>
  <g fill="#f4f3f2" fill-opacity="0.7"><text x="313" y="18">P5</text><text x="370" y="18">P6</text></g>
</svg>
```

### De onde vêm os dados

A raiz é a pasta da sessão: não fixe o caminho do vault no código. Compare caminhos sem diferenciar maiúsculas e aceitando `\` e `/`. Se a pasta da sessão não tiver `_Sistema/` e `Projetos/`, o plugin fica inerte: não abre nem registra nada.

**Ao vivo, nesta sessão.** Os hooks só observam: chamam `next(e)` e devolvem o resultado como veio. Os dois centrais, no formato verificado na 2.1.287:

```ts
on('agent.spawn', async ($, e, next) => {
  const started = await next(e) // { model, agentId } ou { deny }
  // e.subagentType e e.description: quem começou e em quê; started.agentId: o id dele
  return started
})

on('turn.complete', async ($, e, next) => {
  const done = await next(e)
  // com e.agentId: fim de um subagente; e.answer traz o retorno e e.reason o motivo do fim
  // sem e.agentId: fim de turno da conversa principal, hora de reler os arquivos
  return done
})
```

- Início de um agente: o evento de spawn de subagente traz o tipo (`writer`, `form`...) e a descrição curta da tarefa, e o resultado dele traz o id do agente. Marque o agente como trabalhando, com a hora. A lista de agentes da sessão confirma quem está em curso.
- Fim de um agente: o fim de turno do próprio subagente, identificado por esse id, traz a resposta final, que segue um padrão fixo: `STATUS: concluido | parcial | bloqueado`, `ENTREGA`, `RESUMO`, `PENDENCIAS`, `CUSTO`, `MURAL`. concluido vira entregue (2ª linha: o arquivo de ENTREGA). parcial vira entregue, com a pendência na 2ª linha. bloqueado vira bloqueado (2ª linha: a primeira pendência). Turno interrompido ou com erro vira bloqueado, com o motivo "interrompido" ou "erro". Resposta sem STATUS vira entregue, com "retorno fora do padrão".
- Retomada de um agente (mensagem enviada a um agente já iniciado, para uma correção): marque-o como trabalhando de novo; o fim chega do mesmo jeito.
- Dois agentes do mesmo tipo ao mesmo tempo: mostre a tarefa mais recente e "+1".
- Outros tipos de agente (Explore e afins) ficam fora do painel.

**Persistido, no vault (só leitura).**
- `Projetos/<pasta do projeto>/status.md`: fonte dos blocos Projeto, NEEDS YOU, GATES, TASKS e BUDGET (seção "Formatos").
- `Projetos/<pasta do projeto>/mural.md`: cada recado (`AAAA-MM-DD | de → para | recado`) vira uma linha do LOG: "stock deixou um recado para code no mural".
- `_Sistema/academia/`: cada pasta em `cursos/` (`<data>_<agente>_<tema>`) sem linha correspondente em `historico.md` é um curso aberto.

**Estado de cada agente.**
- trabalhando: há um agente desse tipo em curso nesta sessão.
- espera você: uma linha de "Pendências com o José" cita o agente.
- bloqueado ou entregue: o último retorno dele nesta sessão; sem retorno nesta sessão, a última tarefa dele na tabela com status `bloqueado` ou `entregue`.
- livre: nenhum dos anteriores.

Quando mais de um vale, a ordem é esta: trabalhando, espera você, bloqueado, entregue, livre.

**Tarefas ao vivo.** Enquanto um agente trabalha, a linha da tabela com o mesmo agente e o mesmo nome de tarefa (a descrição curta da chamada) aparece como em andamento; quando ele termina, como entregue ou bloqueada. Isso vale até a tabela mudar o status daquela linha. Sem linha correspondente, só o bloco AGENTS mostra o fato.

**GATES.** Aprovado é o portão com linha em "Aprovações" e decisão `aprovado`. Atual é o primeiro ainda não aprovado.

**LOG.** Ao abrir, monte com as últimas aprovações e os últimos recados do mural. Daí em diante, acrescente o que acontecer: entregas, bloqueios, novas aprovações e novos recados.

**Quando reler os arquivos.** Ao abrir o painel, no fim de cada turno da conversa principal e quando uma ferramenta de escrita tocar em um desses arquivos. Sem relógio: nenhum timer fica rodando.

**Projeto atual.** O último projeto em que a sessão escreveu (qualquer arquivo em `Projetos/<pasta>/`); antes disso, o do status.md modificado por último. `/painel <trecho do nome>` fixa um projeto até o fim da sessão. Sem projeto: "Nenhum projeto ativo. Comece com /novo-projeto."

### Formato do status.md (já instalado na Parte 1)

O status.md de cada projeto segue o formato abaixo; as regras estão em `_Sistema/formato-status.md`. Exemplo preenchido:

```markdown
---
cliente: Casa Aurora
projeto: sofá Aria
servico: video-ia
resumo: Vídeo comercial por IA · 30 s · 9:16 e 16:9
etapa: plano de geração
portao: P4 pendente
prazo_entrega: 2026-10-14
modo_geracao: manual
moeda: US$
orcamento_geracao_aprovado:
gasto_geracao: 0
acabamento: José (Premiere/After Effects)
---
# Status do projeto

## Aprovações
| Portão | Data | Decisão | Observação |
|---|---|---|---|
| P3 | 2026-10-02 14:12 | aprovado | |

## Tarefas
| # | Agente | Tarefa | Status | Entrega |
|---|---|---|---|---|
| 5 | code | Plano de geração v1 | entregue | 04_Producao/plano-geracao_v01.md |
| 6 | stock | Inventário e lista de assets | em andamento | |

## Pendências com o José
- P4 | code | Aprovar o plano e o orçamento de geração | 04_Producao/plano-geracao_v01.md | 12 cenas · faixa de US$ 40 a 60

## Pendências com o cliente
- Fotos do sofá em alta resolução | pedido em 2026-10-02
```

- Cabeçalho: uma `chave: valor` por linha. Leia com um leitor simples, sem depender de bibliotecas.
- `etapa`: intake, conceito, roteiro, direção, plano de geração, produção, corte, revisão, ajustes, acabamento, entrega ou retrospectiva.
- `portao`: o primeiro portão ainda não aprovado, como `P4 pendente`; no fim do projeto, `P6 aprovado`.
- `moeda`: `US$`, `R$` ou `créditos`. `orcamento_geracao_aprovado` fica vazio até o P4.
- Decisão: `aprovado`, `ajustes` ou `reprovado`.
- Status das tarefas: `a fazer`, `em andamento`, `entregue` ou `bloqueado`. Coluna Entrega: o caminho do arquivo entregue; em tarefa bloqueada, o motivo em poucas palavras.
- Pendência com o José: `portão | agente | o que decidir | arquivo | detalhe`. O detalhe é opcional; sem portão ou sem agente, use `—`.
- Pendência com o cliente: `o que falta | pedido em AAAA-MM-DD`.
- Datas em `AAAA-MM-DD`, com hora `HH:MM` quando houver. Caminhos relativos à pasta do projeto. Os textos não usam `|`.

### Dados de demonstração (`/painel demo`)

Dados fixos, sem cálculo de datas.

- Projeto: Casa Aurora · sofá Aria. Resumo: Vídeo comercial por IA · 30 s · 9:16 e 16:9. STAGE: Plano de geração. NEXT: P4 · orçamento. DUE: 14/10 · 7 dias úteis.
- NEEDS YOU · 1: "Aprovar o plano e o orçamento de geração". Linha de detalhe: "Portão P4 · 12 cenas · faixa de US$ 40 a 60". Arquivo: 04_Producao/plano-geracao_v01.md. WAITING ON CLIENT: "Fotos do sofá em alta resolução · pedido em 02/10".
- AGENTS: "2 entregues · 1 ativo · 1 espera · 3 livres" e exatamente o SVG de referência.
- GATES: "4 de 7 aprovados" e exatamente o SVG de referência.
- TASKS: "5 de 11". As 11 tarefas, na ordem: ✓ writer · Conceitos v1; ✓ writer · Roteiro e decupagem v1; ✓ writer · Roteiro e decupagem v2; ✓ form · Direção de campanha v1; ✓ code · Plano de geração v1; ● stock · Inventário e lista de assets; ○ code · Fichas de geração (modo manual); ○ code · Corte técnico e timeline XML; ○ visual · Revisão do corte técnico; ○ delivery · Pacote de entrega; ○ skill · Retrospectiva. As 5 linhas visíveis vão de "Roteiro e decupagem v2" a "Fichas de geração (modo manual)".
- LOG: 14:32 stock deixou um recado para code no mural; 14:30 code entregou o plano de geração; 14:12 José aprovou o P3; 13:58 form entregou a direção de campanha.
- BUDGET: a aprovar no P4 · geração em modo manual. ACADEMY: 1 curso aberto · code · higgsfield-api.

### Comandos

- `/painel`: abre o painel no projeto atual.
- `/painel <trecho do nome>`: fixa outro projeto até o fim da sessão.
- `/painel demo`: mostra os dados de demonstração; `/painel` volta aos dados reais.

Os comandos não devolvem texto para a conversa e funcionam mesmo com um turno em andamento. Aviso de comando (projeto não encontrado, por exemplo) sai como aviso rápido da interface. Ao iniciar a sessão, abra o painel sozinho: o Claude Code só o posiciona quando há largura para uma barra lateral.

### Eficiência e segurança

- Os hooks só observam. O painel nunca responde, nega nem reescreve uma ferramenta, um agente, um prompt ou um comando que não seja dele.
- Nada entra na conversa: sem chamadas ao modelo, sem linhas acrescentadas à sessão, sem contexto extra devolvido pelos hooks e sem texto na resposta dos comandos.
- Registre os hooks com filtro (só os eventos e as ferramentas que interessam), para não pesar nas outras chamadas.
- Estado da sessão no estado do plugin, com contrato de tipos. Redesenhe só quando algo mudar.
- No máximo 50 linhas de LOG na memória.
- Leia apenas dentro da pasta da sessão. Nunca escreva no vault, nunca use rede nem rode processos.
- Um erro no painel não pode atrapalhar a conversa: se um arquivo estiver fora do formato, mostre "status.md fora do formato" no bloco e siga.

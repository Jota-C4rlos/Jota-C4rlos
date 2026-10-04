# Pipeline do Orquestrador

Cada etapa termina com um entregável em arquivo e um retorno curto. O orquestrador confere o entregável contra o briefing antes de levar ao José. Caminhos relativos à pasta do projeto; na OS, o orquestrador os escreve a partir da pasta do vault (Projetos/<pasta>/...).

Toda OS de projeto inclui 00_Briefing/briefing.md nas ENTRADAS.

Os comentários e as escolhas do José em cada rodada ou portão ficam em <etapa>/comentarios-jose.md (arquivo de controle, uma seção por data, nas palavras dele), que o orquestrador atualiza e passa nas ENTRADAS. Ex.: 01_Brainstorm/comentarios-jose.md, com os caminhos escolhidos na rodada aberta e o conceito escolhido no P1.

| Etapa | Quem | Entrada | Entrega | Portão |
|---|---|---|---|---|
| 0 Intake e plano | Claude (o pilar ideias prepara a ficha da ideia, se ela vier do Box) | ideia do Box ou nova, insumos | 00_Briefing/briefing.md, viabilidade.md (com o plano) | P0 plano |
| 1 Brainstorm | brainstorm | briefing, ideia, DNAs relacionados, brainstorm feito no Box (se houver) | 01_Brainstorm/brainstorm_v01.md (rodada aberta), conceito_v01.md (rodada fechada) | P1 conceito |
| 2 Roteiro | roteiro (método escolhido) | conceito aprovado | 02_Roteiro/roteiro_v01.md, personagens_v01.md, universo_v01.md | P2 roteiro |
| 3 Construção visual | visual | roteiro, personagens, universo | 03_Visual/estetica_v01.md, personagens-visual_v01.md, cenarios_v01.md, storyboard_v01.md; depois das imagens do José, parecer-visual_v01.md | P3 visual |
| 4 Prompts | prompts (método Take + modelo escolhido) | roteiro, visual aprovado | 04_Prompts/plano-takes_v01.md, takes_v01.md, revisao_v01.md | P4 prompts |
| 5 Geração e ajustes | José gera; prompts ajusta | takes aprovados | 05_Geracao/takes/, log-geracao.md; 04_Prompts/ajustes.md e novas versões dos takes; 05_Geracao/conferencia_vNN.md (quando pedido) | P5 takes |
| 6 Música | musica (começa depois do P2, em paralelo) | roteiro, plano de takes, estética | 06_Musica/musica_v01.md; o José gera e salva em 06_Musica/faixas/; depois, encaixe_v01.md e registro-faixas.md | P6 trilha |
| 7 Retrospectiva | skills | registro de lições, ajustes, pareceres, cadernos | retro.md do projeto + skills sugeridas | o José aprova as mudanças |

## Detalhes por etapa
**0, intake e plano.** /novo-projeto. Se a ideia vier do Box, o pilar ideias prepara a ficha dela com os DNAs relacionados. O plano diz o formato, a duração, a estética provável, os métodos e as ferramentas de cada pilar.

**1, brainstorm.** Duas rodadas. Na aberta, muitos caminhos curtos a partir da ideia, com o que cada um aproveita dos DNAs. O José comenta e escolhe (01_Brainstorm/comentarios-jose.md). Na fechada, de 2 a 3 conceitos desenvolvidos. Cada rodada termina com as perguntas certas ao José.

**2, roteiro.** Pelo método escolhido no catálogo (Pilli Academy quando o material estiver formado; até lá, o roteiro padrão). O roteiro define a trama, as cenas com a duração e os personagens pelo comportamento (objetivo, conflito, jeito de agir e de falar), não pela aparência. O orquestrador confere se o roteiro preserva o conceito, cabe na duração e tem gancho e fechamento.

**3, construção visual.** O José escolhe a estética entre 2 ou 3 opções. O pilar define o visual de cada personagem e cenário e o storyboard, com os prompts de imagem para o Midjourney. O José gera e salva em 03_Visual/imagens/ com o nome indicado. O pilar confere as imagens contra as fichas (consistência e estética) e entrega o parecer. P3 é a validação do visual.

**4, prompts.** Antes de escrever, o pilar faz as perguntas certas (áudio, falas, duração, proporção, imagens de referência). Divide o roteiro em takes dentro da duração máxima do modelo, escreve cada take em mandarim pela estrutura do método Take e revisa continuidade e física (quem sai primeiro, para que lado a porta abre, posição dos personagens, figurino, luz). O José lê a tradução e a revisão em português.

**5, geração e ajustes.** O José gera cada take e salva em 05_Geracao/takes/ com o nome indicado; o orquestrador registra no log-geracao.md. Se houver erro, o José diz qual. O pilar prompts muda só o que deu errado, mantém o que funcionou e devolve o prompt completo, numa nova versão, para gerar do zero. Cada ajuste vira uma linha em 04_Prompts/ajustes.md e em _Sistema/licoes/registro.md. Take aprovado que é ponte por último quadro: o orquestrador pede ao pilar prompts o _fim.png (seção 6 do agente) antes de o José gerar o take seguinte.

**6, música.** O pilar escreve o conceito musical e os prompts (estilo e letra) para a ferramenta escolhida, com as seções no tempo do vídeo. O José gera, ouve e escolhe; o orquestrador registra a faixa escolhida na Observação da linha P6 em Aprovações do status.md.

**7, retrospectiva.** O pilar skills lê as lições e os ajustes do projeto, propõe atualizações de skills (por exemplo, um erro de porta que se repete vira regra no método Take) e entrega retro.md. Nada muda sem o "aprovado" do José.

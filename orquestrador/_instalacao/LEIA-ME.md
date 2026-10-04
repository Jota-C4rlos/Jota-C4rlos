# Kit de instalação — Orquestrador

O escritório já está montado nesta pasta `orquestrador`: as regras, os 7 pilares, as skills e os templates. Este kit explica como usar e guarda as duas partes visuais que ainda se instalam: o painel ao lado da conversa e a rede no segundo monitor.

## Os 7 pilares

| # | Pilar | Agente | O que faz |
|---|---|---|---|
| 1 | Box de Ideias | ideias | guarda ideias e referências; faz o DNA dos vídeos de referência |
| 2 | Brainstorm | brainstorm | desenvolve uma ideia até o conceito |
| 3 | Roteiro | roteiro | trama, cenas e personagens, pelo método escolhido |
| 4 | Construção visual | visual | estética, personagens, cenários e storyboard (Midjourney) |
| 5 | Prompts | prompts | prompts dos takes em mandarim (método Take), revisão e ajustes |
| 6 | Música | musica | trilha e canções (Suno e ElevenLabs) |
| 7 | Skills | skills | cria e atualiza as skills de todos; cursos e retrospectiva |

## Como usar num computador

1. Instale o app desktop do Claude e entre na conta.
2. Copie a pasta `orquestrador` para onde vai ficar o vault (por exemplo `D:\Orquestrador`), ou clone o repositório.
3. Opcional: abra a pasta no Obsidian, para navegar pelas notas.
4. Abra a sessão do Claude Code dentro da pasta `orquestrador`, não na raiz do repositório: só assim ele carrega o CLAUDE.md, os agentes e as skills.
5. Teste de baixo custo: peça para listar os agentes e envie a um deles a ordem "OS teste-00 | brainstorm — OBJETIVO: responder apenas com o formato de retorno padrão, sem ler nem criar arquivos". A resposta deve vir no formato de retorno, o que prova que os padrões foram pré-carregados.
6. Preencha `_Sistema/padroes-prazo-e-preco.md` e `_Sistema/ferramentas-e-contas.md` e, se tiver, coloque suas diretrizes em `Diretrizes/`.

## O dia a dia

- **Guardar uma ideia**: `/ideia` seguido do texto, do link ou do arquivo. Também dá para jogar arquivos direto em `Box_de_Ideias/ideias/`.
- **Analisar uma referência**: salve o vídeo em `Box_de_Ideias/referencias/<categoria>/` (ou o link no `links.md` da categoria) e peça `/dna`.
- **Começar um vídeo**: `/novo-projeto` com a ideia do Box. O orquestrador conduz os portões P0 a P6 e pergunta qual método ou ferramenta usar quando houver mais de um.
- **Mandar material de um método**: arquivos do Pilli Academy em `_Sistema/academia/material/pilli-academy/`; os exemplos do método Take em `_Sistema/academia/material/metodo-take/`. Depois peça para abrir o curso.
- **Ferramenta mudou de versão**: peça ao orquestrador a atualização da skill da ferramenta.

## O que fica fora do git

O `.gitignore` deixa só no seu computador: os projetos, as ideias, as referências e os DNAs do Box, o material dos cursos, os cadernos dos agentes e as mídias (vídeos, imagens, áudios). O repositório guarda só o sistema. Se um dia quiser sincronizar tudo pelo GitHub, use um repositório privado e revise o `.gitignore`.

## Partes visuais (instalar depois)

- **Parte 2, painel** (`2-painel.md`): painel ao lado da conversa com o projeto, o que espera você, os 7 pilares, os portões, as tarefas, o registro, a geração e a academia.
- **Parte 3, rede** (`3-rede.md` + `orquestrador-rede.html`): a mesma informação como uma rede viva, em tela cheia no segundo monitor.

Cada parte é uma sessão nova do Claude Code, aberta na pasta do vault: `Leia o arquivo _instalacao/2-painel.md e siga-o. Eu sou o José.` Só comece a Parte 3 quando a 2 terminar.

## Para gastar menos

- Os pilares já têm o modelo definido no próprio arquivo: Opus nos que mais pedem julgamento (brainstorm, roteiro, visual e prompts) e Sonnet nos demais.
- Na conversa principal, Sonnet com esforço médio resolve o dia a dia. Opus só para destravar, se ele errar duas vezes no mesmo ponto.
- Uma sessão por projeto, do começo ao fim.

## O que o kit não traz

- Diretrizes e material de marca: coloque em `Diretrizes/`.
- Contas e créditos das ferramentas (Midjourney, Seedance, Kling, Suno, ElevenLabs): ficam com você. Chaves de API, se um dia forem usadas, só em variáveis de ambiente.

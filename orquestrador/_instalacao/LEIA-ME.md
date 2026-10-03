# Kit de instalação — Orquestrador

O escritório (Parte 1) já está extraído: os arquivos estão no lugar, nesta pasta `orquestrador`. Este kit guarda o que ainda falta e os modelos para os próximos pilares.

## Situação

- **Parte 1, escritório**: pronta. Pilar 1 (Escrita) definido; pilares 2 a 7 a definir.
- **Parte 2, painel** (`2-painel.md`) e **Parte 3, rede** (`3-rede.md` + `orquestrador-rede.html`): a instalar depois que os 7 pilares estiverem definidos, porque elas desenham os 7 agentes.
- **modelos/**: agentes e documentos do kit original que ainda não foram adotados. Servem de base para os próximos pilares; não estão ativos.

## Como usar num computador

1. Instale o app desktop do Claude e entre na conta.
2. Copie a pasta `orquestrador` para onde vai ficar o vault (por exemplo `D:\Orquestrador`), ou clone o repositório.
3. Opcional: abra a pasta no Obsidian, para navegar pelas notas.
4. Abra a sessão do Claude Code dentro da pasta `orquestrador`, não na raiz do repositório: só assim ele carrega o CLAUDE.md, o agente e as skills.
5. Teste de baixo custo: peça para listar os agentes e envie à escrita a ordem "OS teste-00 | escrita — OBJETIVO: responder apenas com o formato de retorno padrão, sem ler nem criar arquivos". A resposta deve vir no formato de retorno, o que prova que os padrões foram pré-carregados.
6. Preencha `_Sistema/padroes-prazo-e-preco.md`, `_Sistema/ferramentas-e-contas.md` e, se tiver, coloque suas diretrizes em `06_Diretrizes/`.
7. Para começar um trabalho: `/novo-projeto <cliente> <projeto>`.

## Ao definir um novo pilar

1. Crie `.claude/agents/<nome>.md`. Os arquivos em `modelos/agentes/` servem de base: troque a função, mantenha o cabeçalho (`skills: orquestrador-padroes`, `memory: project`, `omitClaudeMd: true`) e use a cor da posição do pilar.
2. Atualize a tabela "Os 7 pilares" e os portões no `CLAUDE.md`.
3. Acrescente as etapas do pilar em `_Sistema/pipeline.md`, as pastas em `/novo-projeto` e, se mudar, as etapas em `_Sistema/formato-status.md`.
4. Registre a mudança em `_Sistema/licoes/changelog.md`.

## Para gastar menos

- Sonnet com esforço médio no dia a dia. Esforço alto só para destravar testes que falharem.
- Opus só para destravar, se ele errar duas vezes no mesmo ponto.
- Uma sessão por projeto, do começo ao fim.

## O que o kit não traz

- Diretrizes e material de marca: coloque em `06_Diretrizes/`.
- Chaves e contas de ferramentas: ficam fora do vault, em variáveis de ambiente.

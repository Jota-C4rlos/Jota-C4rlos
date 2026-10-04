# Academia

A Academia é o pilar 7, o agente skills. Ele cria e atualiza as habilidades (skills) de todos os outros pilares: forma métodos a partir do seu material, atualiza as skills quando uma ferramenta muda, cria métodos alternativos e, no fim de cada projeto, transforma os erros em regras. Nada muda sem o seu "aprovado".

No Windows, a pasta é `_Sistema\academia\`, dentro da pasta do vault.

## O que tem aqui
| Arquivo ou pasta | O que é | Vai para o git? |
|---|---|---|
| `catalogo.md` | as skills de cada pilar, o estado e a data da última mudança | sim |
| `historico.md` | os cursos encerrados | sim |
| `material\<tema>\` | o seu material: aulas, apostilas, exemplos. Cada pasta tem um LEIA-ME dizendo o que pôr | não, só o LEIA-ME |
| `cursos\<data>_<pilar>_<skill>\` | um curso: ementa, rascunho da skill, exercício, respostas do aluno e avaliação | não |
| `propostas\` | as propostas de atualização, as conferências das ferramentas e a revisão dos cadernos, para você aprovar | sim |
| `versoes\` | a cópia de cada skill antes de uma mudança, para voltar atrás se precisar | sim |

As skills ficam em `.claude\skills\<nome>\SKILL.md`. Cada mudança aprovada vira uma linha em `_Sistema\licoes\changelog.md`.

## O catálogo
- **Estados**:
  - `ativa`: pronta para uso.
  - `rascunho`: usável, com as lacunas marcadas.
  - `aguardando material`: não se usa até você mandar o material e o curso terminar.
- **A nota entre parênteses** diz o que falta ou o que o curso espera, como em `rascunho (aguardando os exemplos do José)`. Com um curso aberto, o painel mostra essa nota junto dele.
- **Tipo**: `método` (um jeito de trabalhar, como o método Take) ou `ferramenta` (as regras de uma plataforma, como o Seedance).
- **Opções**: quando um pilar tem mais de uma opção, o orquestrador pergunta qual usar antes de começar, com a recomendação dele: roteiro padrão ou Pilli Academy (quando a skill estiver ativa), Seedance ou Kling, Suno ou ElevenLabs.
- **Atualizada em**: a data da última mudança aprovada.

## Como pedir
Fale com o orquestrador, do seu jeito. Exemplos:

| Você diz | O que acontece |
|---|---|
| "abra o curso do método Take" | curso: forma a skill metodo-take com a sua estrutura e os seus exemplos |
| "abra o curso do Pilli Academy" | curso: forma a skill metodo-pilli-academy com o material do curso |
| "atualize a skill do Seedance" | atualização: compara a skill com as fontes oficiais e traz uma proposta |
| "o Kling 4.0 saiu: atualize o método Kling" | o mesmo, na skill kling |
| "confira se as ferramentas mudaram" | conferência: só um relatório, ferramenta por ferramenta; você escolhe o que atualizar |
| "crie um método novo de roteiro, que funciona assim: ..." | método novo: vira uma opção do pilar no catálogo |
| "quero a estética X" | ficha nova no catálogo de estéticas, com um teste |
| "faça a retrospectiva do projeto X" | retrospectiva; ela já acontece sozinha depois do P6 |
| "revise os cadernos dos agentes" | o que os agentes aprenderam e pode virar regra |
| "volte a versão anterior da skill X" | a cópia guardada em `versoes\` volta a valer |

Antes de um curso, o orquestrador avisa o custo estimado.

## Como funciona um curso
1. Você põe o material em `material\<tema>\` (siga o LEIA-ME da pasta) e pede o curso.
2. O orquestrador avisa o custo. Com o seu ok, o pilar skills abre a pasta do curso em `cursos\`.
3. **Ementa**: o que tem no material, o que falta e o que a skill vai ensinar. As dúvidas chegam para você aqui. Ex.: "posso pôr 2 ou 3 exemplos curtos na skill?".
4. **Rascunho e exercício**: o pilar skills escreve a skill e um exercício pequeno, com dados inventados. O pilar que vai usar a skill, o aluno, faz o exercício. Se errar, o defeito é da skill: o pilar skills corrige e o aluno tenta de novo. No máximo 2 tentativas.
5. **Avaliação**: item por item, ✅ passou · ✨ quase, falta um detalhe · 🔁 não passou.
6. Você lê e responde: "aprovado", "aprovado com ajustes: ..." ou "não".
7. **Formatura**: a skill entra em `.claude\skills\`, o catálogo muda o estado, o curso entra no histórico e a mudança no changelog.

Enquanto o curso está aberto, o painel mostra o pilar, a skill e a nota.

Os cursos previstos:
- **Pilli Academy** → skill metodo-pilli-academy, aluno: roteiro. Até a formatura, os roteiros saem pelo roteiro padrão.
- **Método Take** → skill metodo-take, aluno: prompts. Hoje ela está em rascunho, com uma estrutura provisória; o curso põe a sua estrutura e as regras tiradas dos seus exemplos.

## Atualização de ferramenta
Seedance, Kling, Midjourney, Suno e ElevenLabs mudam rápido: entre o fim de agosto e o fim de setembro de 2026 vieram o Edit Model do Midjourney, o Suno v6, o ElevenLabs Music v2.5 e o anúncio do Kling 4.0. Quando uma ferramenta mudar, ou quando você pedir:
1. O pilar skills lê as fontes oficiais e compara com a skill.
2. Entrega uma proposta em `propostas\`: o que muda, por quê, a fonte e a data, e o impacto nos prompts que já estão em uso.
3. Você aprova tudo ou só alguns itens, pelo número.
4. Ele atualiza a skill, a data no catálogo, o changelog e `_Sistema\ferramentas-e-contas.md`.

Na primeira atualização de cada ferramenta, ele também confere o que as skills marcaram "a confirmar": a pesquisa de 2026-10-04 não conseguiu abrir as páginas oficiais. Alguns itens só você confirma, olhando a tela da plataforma: créditos, opções do Dreamina, o que a sua conta libera.

Projeto em andamento termina na versão da ferramenta em que começou, a não ser que você decida migrar. Teste que gasta créditos só com o seu ok.

## Método novo
Outro método de roteiro, um jeito novo de escrever prompts para outro modelo: o pilar skills monta a skill num curso, com exercício, e na formatura ela entra no catálogo como opção do pilar. A partir daí, o orquestrador pergunta: "roteiro pelo padrão, pelo Pilli Academy ou pelo novo?".

Uma skill por método ou por ferramenta. Ajuste num método que já existe, como o método Kling, é atualização, não skill nova.

## Retrospectiva
Depois do P6, o pilar skills lê o que aconteceu no projeto: as lições registradas, os ajustes dos takes, os pareceres e o status. Entrega `retro.md` na pasta do projeto, com o que funcionou, o que falhou e as mudanças propostas nas skills. Erro que se repete vira regra. Ex.: a porta que abre para o lado errado, se voltar, vira item fixo na revisão de continuidade e no método Take.

## Cadernos dos agentes
Cada agente anota aprendizados técnicos curtos no caderno dele (`.claude\agent-memory\<agente>\MEMORY.md`). De vez em quando, peça a revisão: o que aparece em mais de um caderno vira proposta de regra na skill.

## O que fica fora do git
Só no seu computador:
- `material\`: o material dos cursos e dos seus métodos. Curso tem direitos, e o método Take é seu.
- `cursos\`: os cursos, com rascunhos, exercícios e respostas.
- Os cadernos dos agentes e os projetos, inclusive o retro.md.

Vão para o git: o catálogo, o histórico, as propostas, as versões e as skills. Por isso a skill resume o método com as palavras do pilar skills, sem copiar aulas nem os seus exemplos inteiros. De 2 a 3 exemplos curtos só entram com a sua permissão. Dado de cliente nunca entra em skill.

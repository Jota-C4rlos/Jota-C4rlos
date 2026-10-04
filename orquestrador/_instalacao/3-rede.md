# Parte 3 — Rede de agentes do Orquestrador (página no segundo monitor)

A Parte 2 instalou o painel de agentes ao lado da conversa. Agora você vai instalar a "Orquestrador Network": uma página em tela cheia, para o meu segundo monitor, que mostra os mesmos dados como uma rede viva (Claude no centro, os 7 pilares em volta, partículas correndo nos fios). Eu sou o José, único aprovador.

A página já está pronta e aprovada por mim: `_instalacao\orquestrador-rede.html`, dentro do vault. O seu trabalho é colocá-la no lugar, fazer o painel alimentá-la e criar o atalho.

## Regras desta tarefa

- Isto é instalação do sistema: faça você mesmo, sem delegar aos pilares.
- Não construa nada sem o meu "aprovado" em cada etapa. Comigo, seja conciso, em português, com recomendação clara.
- Não mude o visual nem o comportamento da página. Se achar que precisa mexer nela para ligar os dados, me mostre o trecho e o motivo antes.
- Carregue a skill `plugin-authoring` antes de mexer no plugin. O arquivo de tipos da sua versão é a autoridade; se este prompt divergir dele, valem os tipos, e você me avisa.
- Eu autorizo uma exceção à regra da Parte 2: o painel passa a gravar um único arquivo, `_Sistema/painel/estado.js`. Nada além dele. O painel continua sem chamar o modelo, sem escrever na conversa, sem rede e sem rodar processos.

## Como a página funciona

- Aberta do disco, ela carrega o arquivo `estado.js` da mesma pasta a cada 2 segundos. Esse arquivo tem uma linha: `window.ORQUESTRADOR_STATE = { ... };`.
- Quando o conteúdo muda, ela redesenha a rede mantendo os nós onde estão. Sem o arquivo, mostra dados de demonstração e avisa isso no rodapé.
- O objeto `DEMO`, no começo do script da página, é um exemplo completo do formato, com o mesmo projeto de demonstração da Parte 2 (Canal próprio · A Porta Errada). Use-o como referência.
- A página só reconhece os 7 pilares (`ideias`, `brainstorm`, `roteiro`, `visual`, `prompts`, `musica`, `skills`); agente com outro id é ignorado. Os painéis de baixo, nesta ordem, são `gates`, `tasks`, `log`, `generation` e `academy`; `needs` abre pelo botão largo e pelo nó do José.

## Etapa 0 — Verificação (somente leitura)

1. A Parte 2 está completa, com dados reais e o plugin na pasta definitiva? Diga onde ele mora e se os testes passam. Se faltar algo, pare e me diga.
2. O arquivo `_instalacao\orquestrador-rede.html` existe?
3. Os tipos da sua versão trazem a escrita de arquivo pelo plugin, um disparo único de relógio e o evento de fim de sessão?
4. Qual navegador abre uma página em janela própria nesta máquina (Edge ou Chrome)?
5. Me apresente um plano em até 12 linhas e espere meu "aprovado".

## Etapa 1 — Página no lugar

1. Copie a página para `_Sistema\painel\rede.html`. É cópia: deixe o original em `_instalacao` como está.
2. Grave à mão um `_Sistema\painel\estado.js` de teste, no formato abaixo, com o projeto atual (ou com um exemplo claramente marcado como teste, se não houver projeto).
3. Me diga para abrir a página e conferir: ela deve mostrar o estado de teste, sem o aviso de demonstração. Espere meu "aprovado". O arquivo de teste será sobrescrito pelo painel na Etapa 2.

## Etapa 2 — O painel grava o estado

Sempre que mudar algo que o painel mostra, monte o estado e grave o `estado.js`.

- Junte mudanças próximas: no máximo uma gravação por segundo, com um disparo único de relógio. Nenhum relógio contínuo. Grave só quando o texto for diferente do último gravado.
- No fim da sessão, grave uma última vez com `session: "encerrada"`.
- O arquivo é `window.ORQUESTRADOR_STATE = ` seguido do estado em JSON e de `;`.

Dados novos a coletar, sempre só observando (os hooks seguem devolvendo o resultado como veio):

- **Ordem de serviço de cada agente**: do texto da chamada do agente, as linhas `OS`, `OBJETIVO`, `MÉTODO`, `ENTRADAS`, `ENTREGA`, `ACEITE` e `LIMITES`.
- **Atividade de cada agente**: as chamadas de ferramenta feitas dentro do agente, com a hora (HH:MM). Leitura vira "Leu <arquivo>", escrita "Escreveu <arquivo>", edição "Editou <arquivo>", busca "Procurou <termo>", comando "Rodou um comando", web "Pesquisou na web", skill "Usou a skill <nome>". Guarde as 30 últimas por agente. Só nomes de arquivo, nunca o conteúdo.
- **Retorno**: quando o agente termina, uma linha "Entregou" (ou "Bloqueado"), com o RESUMO e as PENDENCIAS no subtexto e o CUSTO na marca.
- **Recados do mural**: os 3 últimos de hoje, com origem, destino, hora (quando vistos ao vivo) e texto.
- **Exercícios de curso**: o orquestrador chama o aluno com a ordem que o pilar skills preparou (descrição "Exercício <skill> tNN"); a atividade e o retorno do aluno entram nele como em qualquer chamada.

A atividade e a ordem de serviço só existem durante a sessão. Ao abrir uma sessão nova, o agente mostra o que o status.md permite: entregas, tarefa em curso e próxima tarefa.

### Formato do estado

```js
window.ORQUESTRADOR_STATE = {
  session: "ativa",                 // ou "encerrada"
  clock: "14:33",                   // hora da última mudança
  project: { title: "Canal próprio · A Porta Errada", line: "Prompts · próximo portão: P4 prompts · entrega em 14/10, 7 dias úteis",
             client: "Canal próprio", clientTip: ["Canal próprio", "Projeto próprio: nada pendente com o cliente"] },
  needs: { count: 1, gate: "P4", text: "Aprovar os prompts dos takes", agent: "prompts" },
  messages: [{ from: "prompts", to: "musica", time: "14:31", text: "Take 4 tem 8 s sem fala antes da virada: a música pode crescer ali." }],
  agents: [ /* os 7, sempre nesta ordem: ideias, brainstorm, roteiro, visual, prompts, musica, skills */
    { id: "musica", role: "trilha no Suno e no ElevenLabs",
      state: "trabalhando",         // livre | trabalhando | espera | entregue | bloqueado
      label: "trabalhando",         // texto sob o nome; em espera: "espera você · P4"
      headline: "Trabalhando desde 14:28",
      tip: ["Trabalhando desde 14:28", "Música v1", "Agora: escrevendo musica_v01.md"],
      files: [],                    // nomes das entregas neste projeto, no máximo 5
      courses: [],                  // só no skills: [{ name: "metodo-take", student: "prompts" }]
      rows: [ ["h", "Ordem de serviço em curso"], ["OS", "porta-errada-09", "Música v1"], ["Método", "suno"],
              ["h", "Atividade ao vivo"], ["14:29", "Leu roteiro_v02.md"], ["14:33", "Escrevendo musica_v01.md", "", "agora"] ] }
  ],
  panels: {
    needs:      { kicker: "Needs you", title: "O que espera você", state: "1 decisão sua", rows: [] },
    gates:      { kicker: "Gates", title: "Portões", state: "4 de 7 aprovados", chip: ["Gates", "4 de 7", "atual: P4"], tip: ["Portão atual: P4 prompts"], rows: [] },
    tasks:      { /* mesmo formato */ }, log: { }, generation: { }, academy: { }
  }
};
```

- `role` é a função curta de cada pilar, sempre esta: ideias "ideias, referências e DNA dos vídeos"; brainstorm "brainstorm em cima da ideia"; roteiro "trama, cenas e personagens"; visual "estética, personagens, cenários e storyboard"; prompts "prompts em mandarim, continuidade e ajustes"; musica "trilha no Suno e no ElevenLabs"; skills "skills, cursos e retrospectiva".
- `project.client`: o nome do cliente; em projeto próprio (`cliente: proprio`), "Canal próprio", com `clientTip` dizendo que não há pendência com cliente.
- `generation`: o bloco GENERATION da Parte 2. Chip `["Generation", "N de M", "<modelo_video>"]` (ou `["Generation", "depois do P4", "takes no <modelo_video>"]` antes de a tabela Takes ter linhas); nas `rows`, um take por linha (take, status, tentativas e arquivo) e os modelos escolhidos. Com take em `ajuste`, diga quantos no chip.
- `academy`: os cursos abertos (`pilar · tema`, com a nota), as skills `aguardando material` do catálogo e as skills fixas.
- Sem projeto ativo: omita `project`, mande `needs: { count: 0 }`, os 7 pilares como `livre` e os painéis que fizerem sentido (em geral, `academy`, que não depende de projeto). A página mostra "Nenhum projeto ativo" e "Comece com /novo-projeto no Claude Code".
- Linha de `rows`: `["h", "Título da seção"]` ou `[chave, texto, subtexto, marca, endereço]`. Só chave e texto são obrigatórios. A marca `"agora"` destaca a linha.
- `chip` são os três textos do bloco na base da tela; `tip` é o cartão que aparece ao passar o mouse.
- O estado de cada agente segue as mesmas regras do painel da Parte 2.
- Endereço: `obsidian://open?path=` mais o caminho absoluto do arquivo, codificado. Faz o item "abrir" abrir a nota no Obsidian. Teste um; se não abrir, use um endereço `file:`. A página só aceita esses dois tipos.

Testes com `claude plugin test`: o estado gerado sem projeto, com agente trabalhando, entregue, bloqueado e esperando por mim, com a tabela Takes vazia e com um take em ajuste; o arquivo só é gravado quando muda; os hooks continuam devolvendo o resultado sem alterar nada. Depois me peça para olhar a página com uma sessão real e espere meu "aprovado".

## Etapa 3 — Atalho na área de trabalho

1. Crie o atalho "Orquestrador Network" na minha Área de Trabalho, abrindo `_Sistema\painel\rede.html` em janela própria, sem barra de navegador. Isso escreve fora do vault: me mostre o comando exato e o destino antes, e espere meu ok.
2. Ícone: se houver um `.ico` do Orquestrador no vault, use-o. Não converta nem crie imagem sem me perguntar.
3. Me entregue um resumo em até 10 linhas: onde ficou cada arquivo, como pôr a janela no segundo monitor em tela cheia, o que a página mostra com o Claude Code fechado e como desfazer tudo.

## Eficiência e segurança

- Nada disso gasta tokens: gravar o arquivo e desenhar a página não passam pelo modelo.
- O `estado.js` tem dados dos projetos e fica só neste computador (o `.gitignore` já o deixa fora do git). Não o envie a lugar nenhum.
- Um erro ao gravar o arquivo não pode atrapalhar a conversa nem o painel: registre e siga.
- Registre os hooks novos com filtro e mantenha cada um curto, porque a atividade observa todas as ferramentas dos agentes.

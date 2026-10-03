# Parte 3 — Rede de agentes do Orquestrador (página no segundo monitor)

> **Pendente — adaptar antes de instalar.** Este documento veio do kit original e ainda descreve os 7 agentes de lá (writer, form, stock, code, visual, delivery, skill), os portões P3 a P6 e os campos de geração por IA. Quando os 7 pilares do Orquestrador estiverem definidos, troque nomes, funções e dados de demonstração pelos novos. A geometria, as cores por posição e as regras de comportamento continuam valendo.

A Parte 2 instalou o painel de agentes ao lado da conversa. Agora você vai instalar a "Orquestrador Network": uma página em tela cheia, para o meu segundo monitor, que mostra os mesmos dados como uma rede viva (Claude no centro, os 7 agentes em volta, partículas correndo nos fios). Eu sou o José, único aprovador.

A página já está pronta e aprovada por mim: `_instalacao\orquestrador-rede.html`, dentro do vault. O seu trabalho é colocá-la no lugar, fazer o painel alimentá-la e criar o atalho.

## Regras desta tarefa

- Isto é instalação do sistema: faça você mesmo, sem delegar aos agentes.
- Não construa nada sem o meu "aprovado" em cada etapa. Comigo, seja conciso, em português, com recomendação clara.
- Não mude o visual nem o comportamento da página. Se achar que precisa mexer nela para ligar os dados, me mostre o trecho e o motivo antes.
- Carregue a skill `plugin-authoring` antes de mexer no plugin. O arquivo de tipos da sua versão é a autoridade; se este prompt divergir dele, valem os tipos, e você me avisa.
- Eu autorizo uma exceção à regra da Parte 2: o painel passa a gravar um único arquivo, `_Sistema/painel/estado.js`. Nada além dele. O painel continua sem chamar o modelo, sem escrever na conversa, sem rede e sem rodar processos.

## Como a página funciona

- Aberta do disco, ela carrega o arquivo `estado.js` da mesma pasta a cada 2 segundos. Esse arquivo tem uma linha: `window.ORQUESTRADOR_STATE = { ... };`.
- Quando o conteúdo muda, ela redesenha a rede mantendo os nós onde estão. Sem o arquivo, mostra dados de demonstração e avisa isso no rodapé.
- O objeto `DEMO`, no começo do script da página, é um exemplo completo do formato. Use-o como referência.

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

- **Ordem de serviço de cada agente**: do texto da chamada do agente, as linhas `OS`, `OBJETIVO`, `ENTRADAS`, `ENTREGA`, `ACEITE` e `LIMITES`.
- **Atividade de cada agente**: as chamadas de ferramenta feitas dentro do agente, com a hora (HH:MM). Leitura vira "Leu <arquivo>", escrita "Escreveu <arquivo>", edição "Editou <arquivo>", busca "Procurou <termo>", comando "Rodou um comando", web "Pesquisou na web", skill "Usou a skill <nome>". Guarde as 30 últimas por agente. Só nomes de arquivo, nunca o conteúdo.
- **Retorno**: quando o agente termina, uma linha "Entregou" (ou "Bloqueado"), com o RESUMO e as PENDENCIAS no subtexto e o CUSTO na marca.
- **Recados do mural**: os 3 últimos de hoje, com origem, destino, hora (quando vistos ao vivo) e texto.

A atividade e a ordem de serviço só existem durante a sessão. Ao abrir uma sessão nova, o agente mostra o que o status.md permite: entregas, tarefa em curso e próxima tarefa.

### Formato do estado

```js
window.ORQUESTRADOR_STATE = {
  session: "ativa",                 // ou "encerrada"
  clock: "14:33",                   // hora da última mudança
  project: { title: "Casa Aurora · sofá Aria", line: "Plano de geração · próximo portão: P4 orçamento · entrega em 14/10, 7 dias úteis",
             client: "Casa Aurora", clientTip: ["1 pendência com o cliente", "Fotos do sofá em alta resolução, pedido em 02/10"] },
  needs: { count: 1, gate: "P4", text: "Aprovar o plano e o orçamento de geração", agent: "code" },
  messages: [{ from: "stock", to: "code", time: "14:32", text: "..." }],
  agents: [ /* os 7, sempre nesta ordem: writer, form, stock, code, visual, delivery, skill */
    { id: "stock", role: "biblioteca, inventário e assets base",
      state: "trabalhando",         // livre | trabalhando | espera | entregue | bloqueado
      label: "trabalhando",         // texto sob o nome; em espera: "espera você · P4"
      headline: "Trabalhando desde 14:28",
      tip: ["Trabalhando desde 14:28", "Inventário e lista de assets", "Agora: escrevendo inventario.md"],
      files: ["inventario.md"],     // nomes das entregas neste projeto, no máximo 5
      courses: [],                  // só na skill: [{ name: "higgsfield-api", student: "code" }]
      rows: [ ["h", "Ordem de serviço em curso"], ["OS", "aurora-06", "Inventário e lista de assets"],
              ["h", "Atividade ao vivo"], ["14:29", "Leu decupagem_v02.md"], ["14:33", "Escrevendo inventario.md", "", "agora"] ] }
  ],
  panels: {
    needs:   { kicker: "Needs you", title: "O que espera você", state: "1 decisão sua · 1 pendência com o cliente", rows: [] },
    gates:   { kicker: "Gates", title: "Portões", state: "4 de 7 aprovados", chip: ["Gates", "4 de 7", "atual: P4"], tip: ["Portão atual: P4 orçamento"], rows: [] },
    tasks:   { /* mesmo formato */ }, log: { }, budget: { }, academy: { }
  }
};
```

- Sem projeto ativo: omita `project`, mande `needs: { count: 0 }`, os 7 agentes como `livre` e os painéis que fizerem sentido.
- Linha de `rows`: `["h", "Título da seção"]` ou `[chave, texto, subtexto, marca, endereço]`. Só chave e texto são obrigatórios. A marca `"agora"` destaca a linha.
- `chip` são os três textos do bloco na base da tela; `tip` é o cartão que aparece ao passar o mouse.
- O estado de cada agente segue as mesmas regras do painel da Parte 2.
- Endereço: `obsidian://open?path=` mais o caminho absoluto do arquivo, codificado. Faz o item "abrir" abrir a nota no Obsidian. Teste um; se não abrir, use um endereço `file:`. A página só aceita esses dois tipos.

Testes com `claude plugin test`: o estado gerado sem projeto, com agente trabalhando, entregue, bloqueado e esperando por mim; o arquivo só é gravado quando muda; os hooks continuam devolvendo o resultado sem alterar nada. Depois me peça para olhar a página com uma sessão real e espere meu "aprovado".

## Etapa 3 — Atalho na área de trabalho

1. Crie o atalho "Orquestrador Network" na minha Área de Trabalho, abrindo `_Sistema\painel\rede.html` em janela própria, sem barra de navegador. Isso escreve fora do vault: me mostre o comando exato e o destino antes, e espere meu ok.
2. Ícone: se houver um `.ico` do Orquestrador no vault, use-o. Não converta nem crie imagem sem me perguntar.
3. Me entregue um resumo em até 10 linhas: onde ficou cada arquivo, como pôr a janela no segundo monitor em tela cheia, o que a página mostra com o Claude Code fechado e como desfazer tudo.

## Eficiência e segurança

- Nada disso gasta tokens: gravar o arquivo e desenhar a página não passam pelo modelo.
- O `estado.js` tem dados do projeto do cliente e fica só neste computador. Não o envie a lugar nenhum.
- Um erro ao gravar o arquivo não pode atrapalhar a conversa nem o painel: registre e siga.
- Registre os hooks novos com filtro e mantenha cada um curto, porque a atividade observa todas as ferramentas dos agentes.

# Pipeline — vídeo comercial por IA

Cada etapa termina com um entregável em arquivo e um retorno curto. O orquestrador confere o entregável contra o briefing antes de levar ao José.

| Etapa | Quem | Entrada | Entrega | Portão |
|---|---|---|---|---|
| 0 Intake e viabilidade | Claude | insumos do José | 00_Briefing/briefing.md, viabilidade.md | P0 |
| 1 Conceito | writer | briefing | 01_Roteiro/conceitos_v01.md (2 a 3 caminhos) | P1 |
| 2 Roteiro e decupagem | writer | conceito escolhido | 01_Roteiro/roteiro_v01.md, decupagem_v01.md | P2 |
| 3 Direção de campanha | form | briefing e conceito (pode começar após o P1, em paralelo à etapa 2) | 02_Direcao/direcao-campanha_v01.md | P3 |
| 4 Plano de geração | stock + code | decupagem e direção | 03_Assets/inventario.md, 04_Producao/plano-geracao_v01.md | P4 |
| 5 Produção | stock, depois code (e o José, no modo manual) | P4 aprovado | assets base, cenas em 04_Producao/cenas/, log-geracao.md | — |
| 6 Corte técnico | code | cenas e decupagem | 04_Producao/montagem/corte_v01.mp4 + timeline_v01.xml | — |
| 7 Revisão | visual | corte, direção e decupagem | 05_Revisao/parecer_v01.md | — |
| 8 Ajustes | code e stock | parecer | novas versões | P5 (o José assiste ao corte) |
| 9 Acabamento fino | José | corte aprovado + timeline XML | master em 04_Producao/master/ | — |
| 10 Entrega | delivery | master e briefing | 06_Entrega/ + entrega.md | P6 |
| 11 Retrospectiva | skill (Academia) | registro de lições, pareceres e cadernos | retro.md do projeto + cursos sugeridos | o José aprova cursos e formaturas |

## Detalhes por etapa
**1 e 2, writer.** Primeiro identifica o que é inegociável na ideia do cliente. Conceitos curtos; o roteiro completo só depois do P1. O orquestrador acompanha: confere se o roteiro preserva os inegociáveis, cabe na duração e tem gancho e CTA.

**3, form.** Define as regras visuais que todos seguem. Se o José quiser, o stock gera de 2 a 3 style frames antes do P3 (custo pequeno, pedir aprovação antes).

**4, plano de geração.** O stock lista o que existe, o que gerar e o que licenciar, sem gastar. O code escreve os prompts por cena, escolhe ferramenta e modelo e estima o custo com margem de refação. Apresente P3 e P4 juntos quando possível.

**5, produção.** Gasto só dentro do P4. Modo manual (padrão até a API): o code entrega as fichas por cena, o José gera na plataforma e salva em 04_Producao/cenas/ com o nome da ficha, e o code confere e registra no log. Modo API: o code executa e registra.

**6, corte técnico.** O code monta o corte com ffmpeg seguindo a decupagem e exporta a timeline em XML para o Premiere. Logo, textos de tela e packshot são compostos, não gerados por IA.

**7 e 8, revisão.** O visual revisa por contact sheets e frames-chave; ritmo e movimento são validados pelo José no P5. Refações voltam ao code com instrução concreta. Se a refação estourar o orçamento, consulte o José.

**9, acabamento fino.** O José abre a timeline XML no Premiere/After Effects e faz motion graphics, cor final, mixagem, ajustes de ritmo, composição, legendas e exportação por plataforma. Se ele quiser, o visual revisa o master antes da entrega.

**10, delivery.** Prepara, confere e escreve a mensagem. O José envia.

**11, Academia.** Faz a retrospectiva, revisa os cadernos e sugere cursos. Nada muda sem aprovação.

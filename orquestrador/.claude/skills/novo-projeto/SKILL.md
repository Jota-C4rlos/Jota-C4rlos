---
name: novo-projeto
description: Inicia um projeto do Orquestrador - intake, ficha da ideia, viabilidade e plano para o portão P0. Use quando o José quiser transformar uma ideia (do Box ou nova) num vídeo.
argument-hint: ideia do Box ou nome do projeto
---
# Novo projeto

Esta etapa é sua: não delegue o intake nem a viabilidade.

1. **Ideia**: se o José citou uma ideia do Box, encontre-a em Box_de_Ideias/indice.md. Se for uma ideia nova, registre-a antes no Box com /ideia.
2. **Pasta**: crie Projetos/<AAAA-MM>_<cliente-ou-canal>_<projeto>/ com:
   ```
   00_Briefing/insumos/
   01_Brainstorm/
   02_Roteiro/
   03_Visual/imagens/
   04_Prompts/
   05_Geracao/takes/
   06_Musica/faixas/
   ```
   Use "proprio" no lugar do cliente quando o conteúdo for do José. Copie _Sistema/templates/status.md para a raiz do projeto e preencha o cabeçalho. Crie também mural.md na raiz, com a linha "# Mural — recados entre agentes". No Box, mude o status da ideia, na nota e no índice, para `em projeto (Projetos/<pasta>/)`. Se a ideia veio do Box, peça ao pilar ideias a ficha da ideia (OS curta: ENTREGA Projetos/<pasta>/00_Briefing/ficha-ideia.md); ele também procura os DNAs relacionados que a nota não cita. Se houver um brainstorm feito no Box (Box_de_Ideias/ideias/<nome-da-nota>_brainstorm_vNN.md), anote o caminho no briefing, para a etapa 1.
3. **Insumos**: textos, áudios, imagens e documentos que o José mandou vão para 00_Briefing/insumos/. Não altere nada.
4. **Briefing**: preencha 00_Briefing/briefing.md a partir de _Sistema/templates/briefing.md. Marque cada campo como ok, faltando ou suposição. Não invente dados.
5. **Lacunas**: faltando item obrigatório, faça as perguntas certas ao José (máx. 4 por rodada, com sugestão de resposta).
6. **Viabilidade**: com o briefing completo, siga _Sistema/checklist-viabilidade.md e escreva 00_Briefing/viabilidade.md (máx. 1 página).
7. **Plano**: na mesma nota, o plano macro: etapas, prazos internos, portões, quantidade estimada de takes e o método ou a ferramenta de cada pilar, conforme o catálogo (_Sistema/academia/catalogo.md). Onde houver mais de uma opção, traga sua recomendação para o José escolher.
8. **P0**: apresente ao José em até 12 linhas: veredito (seguir, seguir com ressalvas ou não seguir), pontos de atenção e decisões que ele precisa tomar. Espere o "aprovado".
9. **Aprovado**: registre no status.md (aprovação, métodos escolhidos, tarefas), leia _Sistema/pipeline.md e siga para a etapa 1 (brainstorm).

---
name: novo-projeto
description: Inicia um projeto do Orquestrador - intake do briefing, relatório de viabilidade e plano para o portão P0. Use quando o José trouxer um novo trabalho de cliente.
argument-hint: cliente e nome do projeto
---
# Novo projeto

Esta etapa é sua: não delegue o intake nem a viabilidade.

1. **Pasta**: crie Projetos/<AAAA-MM>_<cliente>_<projeto>/ com:
   ```
   00_Briefing/insumos/
   01_Roteiro/
   03_Assets/cliente/original/
   ```
   As demais pastas (02, 04 a 06) entram quando os próximos pilares forem definidos.
   Copie _Sistema/templates/status.md para a raiz do projeto e preencha o cabeçalho. Crie também mural.md na raiz, com a linha "# Mural — recados entre agentes".
2. **Insumos**: textos e documentos que o José mandou vão para 00_Briefing/insumos/. Mídia e marca do cliente (imagens, vídeos, logos, fontes, manual de marca) vão para 03_Assets/cliente/original/. Não altere nada.
3. **Briefing**: preencha 00_Briefing/briefing.md a partir de _Sistema/templates/briefing.md. Marque cada campo como ok, faltando ou suposição. Não invente dados.
4. **Lacunas**: faltando item obrigatório, pare e pergunte ao José (máx. 4 perguntas por rodada, com sugestão de resposta quando possível).
5. **Viabilidade**: com o briefing completo, siga _Sistema/checklist-viabilidade.md e escreva 00_Briefing/viabilidade.md (máx. 1 página).
6. **Plano**: na mesma nota, o plano macro: etapas, pilares envolvidos, prazos internos e portões. Se o projeto pedir um pilar ainda não definido, diga qual trabalho ficaria sem dono.
7. **P0**: apresente ao José em até 12 linhas: veredito (seguir, seguir com ressalvas ou não seguir), pontos de atenção e decisões que ele precisa tomar. Espere o "aprovado".
8. **Aprovado**: registre no status.md, leia _Sistema/pipeline.md e siga para a etapa 1 (escrita).

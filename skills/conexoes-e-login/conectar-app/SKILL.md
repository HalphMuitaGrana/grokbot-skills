---
name: conectar-app
description: "Quando a pessoa pede para ligar um app ao bot (Gmail, Agenda, Notion, Slack, Instagram...) ou a tarefa precisa de um app que ainda não está conectado."
---

# Conectar um app

## Processo

1. **Qual app:** o que a pessoa disse. Se ela não disse e mais de um serve (Gmail ou Outlook, Google Agenda ou Outlook),
   pergunte num cartão (`show_widget`) com as opções reais.
2. **Já está conectado?** Veja nas conexões do Composio. Conectado e funcionando: diga e siga com a tarefa. Conectado mas
   pedindo login de novo: peça o login (passo 3).
3. **Conectar:** peça a conexão com `COMPOSIO_MANAGE_CONNECTIONS` (ou o login do servidor MCP, para um servidor MCP). O
   cartão de conectar aparece no chat: ele **é** a pergunta, então não pergunte antes "quer que eu conecte?".
   - Uma segunda conta do mesmo app (outro Gmail, outro Instagram): dê um nome à conta (o apelido) no pedido.
   - Nunca cole o link de autorização no chat: o cartão abre a página certa.
4. **Esperar:** termine o que não depende do app e encerre a vez. Quando a pessoa conecta, o bot volta sozinho; não
   peça para ela avisar.
5. **Não existe conexão para o app:** siga a habilidade `sem-conexao`.

## Caixa

- Uma conexão por pedido, um cartão por app que falta.
- Desconectar ou trocar a conta conectada mexe na conta da pessoa: só com o "sim" dela num cartão.
- O app só fica disponível para os bots que a pessoa liberou no acesso do bot; se ele estiver fechado para este bot,
  diga isso em vez de pedir de novo.

## Prova

- Depois do cartão, a conexão aparece como conectada e a tarefa seguiu.

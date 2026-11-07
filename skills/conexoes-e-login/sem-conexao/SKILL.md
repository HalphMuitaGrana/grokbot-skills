---
name: sem-conexao
description: "Quando a tarefa precisa de um serviço que não tem conexão (um site, um painel, um chat como WhatsApp ou Instagram, um programa de linha de comando que pede login). Use antes de dizer que não consegue."
---

# Serviço sem conexão

A pessoa já pediu a tarefa: isso já é o "sim" para alcançar o serviço. Não pergunte se pode tentar; tente pelo caminho
seguro e pergunte só o que só ela pode fazer (o login).

## Processo

1. **Confirme que não há conexão** para nenhum serviço que a tarefa toca, não só o principal. Existindo uma, siga
   `conectar-app`: dados por conexão valem mais que ler uma tela.
2. **Abra o serviço no navegador do bot** (`browser_open`, `browser_navigate`) e siga `navegador-do-bot`.
3. **Na tela de login,** siga `login-e-dados-privados`. Esse é o único passo que você mostra à pessoa antes.
4. **Logado, faça o trabalho** e diga o que encontrou.
5. **Programas de linha de comando** que pedem login (`gh` do GitHub, por exemplo): comece o login você mesmo. O que
   pedir senha, código ou aprovação no navegador vira um pedido à pessoa (`request_sign_in`). O login fica guardado e
   serve às próximas vezes.
6. **Mandar como a pessoa:** quando uma conexão manda mensagens "como app" e precisa sair em nome dela, use o navegador
   onde ela está logada, com a confirmação de `mandar-em-seu-nome`.

## Caixa

- Não mande a pessoa colar os dados ou fazer print se o bot consegue chegar lá; ofereça isso só se não der mesmo.
- Nunca use o navegador como atalho em volta de uma conexão quebrada: diga o que falhou e o que conserta.

## Prova

- Ou a tarefa foi feita, ou a pessoa recebeu um cartão de login dizendo o que falta, nunca só um aviso em texto.

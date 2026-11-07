---
name: login-e-dados-privados
description: "Antes de entrar num site, de usar um código de confirmação (2FA, SMS, e-mail) ou de qualquer página que peça senha, cartão ou outro dado que só a pessoa tem."
---

# Login e dados privados

Siga a ordem e pare no primeiro passo que funcionar.

## Processo

1. **Login salvo:** se a pessoa salvou o login no Bots ou tem o 1Password ligado, use `fill_login` na página de login
   aberta. O bot nunca vê a senha.
2. **A pessoa entra:** sem login salvo, peça com `request_sign_in` (cartão e aviso; ela entra na tela onde o bot
   trabalha e aperta Pronto). Também para passkey, QR code, aprovação em outro aparelho, captcha que você tentou e não
   passou, e confirmação do banco.
3. **Chave ou senha que o bot precisa guardar** (a chave de um serviço, uma caixa de e-mail): `request_credential`,
   num cartão seguro.

## Google

- **Nunca entre numa conta Google pelo navegador do bot.** O Google bloqueia navegador automático ("este navegador pode
  não ser seguro"), e contas de empresa pedem aparelho aprovado.
- Use a conexão do Gmail, da Agenda ou do Drive (`COMPOSIO_MANAGE_CONNECTIONS`): o cartão de conectar abre o login no
  navegador da própria pessoa.
- Se o navegador já caiu na página de recusa do Google, pare ali e faça o mesmo.

## Códigos de confirmação

- Código que o site manda para o e-mail da pessoa, num login que ela pediu: se o e-mail dela está ligado, leia você
  mesmo a mensagem mais nova daquele site e digite o código. Não pergunte.
- Captcha simples ("não sou robô", segurar o botão): tente você primeiro. Só peça ajuda se não passar.

## Caixa

- Nunca peça senha, código ou número de cartão no chat.
- Se a pessoa mandou um dado no chat mesmo assim, use para aquela tarefa e não repita o valor nas respostas.
- Depois de entrar, confira que está logado antes de seguir.

## Prova

- A página seguinte ao login mostra a conta da pessoa.
- Nenhum valor secreto aparece nas mensagens do bot.

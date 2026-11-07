---
name: pagamentos
description: "Sempre que for pagar, reservar com cartão ou finalizar um pedido, e quando a pessoa falar de cartão de crédito. Leia antes da página de pagamento."
---

# Pagamentos

O bot nunca gasta sozinho. Cada compra tem a sua aprovação, e o número do cartão nunca passa pelo bot.

## Processo

1. **Ler o total de verdade** na página final da loja: produto ou serviço, quantidade, frete, taxas, impostos e total.
2. **Aprovar:** **um cartão** (`show_widget`) com o que está sendo comprado, a loja, o endereço ou a data, e o **total
   exato daquela página**. Fechar o cartão sem responder é "não". Uma recusa é final para aquela compra.
3. **Pagar, nesta ordem, parando no primeiro que funciona:**
   - a forma de pagamento já salva na conta da loja;
   - a pessoa paga ela mesma, na tela onde o bot trabalha (`request_sign_in`), quando não há forma salva ou a loja pede
     confirmação do banco.
4. **Conferir antes de dizer "comprei":** a página de confirmação, o número do pedido e o total cobrado.

## Caixa

- O "sim" vale para uma compra, um carrinho e um total. Mudou o total depois do "sim" (frete, tarifa dinâmica, uma troca
  de item): pare, mostre os dois valores e peça de novo.
- **Nunca peça número de cartão, código de segurança ou validade no chat**, nem escreva esses dados numa mensagem,
  arquivo ou registro.
- Se a pessoa colar um cartão no chat mesmo assim, não repita o número; diga que ele deve ser posto na tela de
  pagamento.
- Depois de uma compra que falhou ou demorou, confira se o pedido passou (página de confirmação, histórico da loja,
  e-mail) antes de tentar de novo: tentar de novo pode cobrar duas vezes.

## Prova

- Existe um cartão aprovado com o mesmo total da página final, e o número do pedido confere.

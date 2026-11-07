---
name: mercado
description: "Quando a pessoa pede compra de supermercado para entregar: a lista da semana, os ingredientes de uma receita, a reposição de sempre."
---

# Mercado

## Processo

1. **Onde:** o mercado que a pessoa disse ou usa sempre (memória); sem isso, pergunte.
2. **A lista antes da loja:** a "lista de sempre" da memória, mais o que ela pediu. Receita vira lista pelas porções, sem
   o que ela já tem; diga o que deixou de fora (sal, óleo).
3. **Montar de uma vez:** abra a loja e procure a lista toda numa passada (`navegador-do-bot`). Para cada item: o de
   sempre, um parecido (outra marca ou tamanho) ou não encontrado, com o preço.
4. **Perguntar uma vez:** tudo o que ficou parecido ou faltou, numa pergunta só, já com a escolha proposta.
5. **Mínimo de entrega:** abaixo dele, diga quanto falta, sem completar sozinho.
6. **Substituições:** a regra que a pessoa deu; sem regra, nada de substituto em item de alergia ou dieta, e "o mais
   parecido" no resto, dizendo o que escolheu.
7. **Horário de entrega:** mostre as opções; ela escolhe.
8. **Aprovar e pagar:** leia o checkout (itens, taxas, gorjeta, total, endereço, horário) e siga `pagamentos`.
9. **Depois:** ofereça uma vez guardar a lista como "a de sempre" daquele mercado, e uma rotina semanal que monta o
   carrinho e pede o "sim" a cada vez.

## Caixa

- Endereço confirmado sempre, mesmo com um salvo.
- O total do mercado é uma estimativa (item por peso, trocas): diga isso.
- Promoção que depende de cartão fidelidade ou de quantidade mínima só conta se o carrinho cumprir.
- Recuse teste de assinatura, entrega expressa e "arredondar o troco" que ela não pediu.
- Nunca invente produto, preço, oferta ou horário.

## Prova

- O carrinho tem só a lista aprovada, e o cartão de pagamento foi aprovado com o total do checkout.

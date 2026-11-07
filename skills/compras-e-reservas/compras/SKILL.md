---
name: compras
description: "Quando a pessoa pede para procurar, comparar ou comprar um produto numa loja online (Mercado Livre, Amazon, Shopee, Magalu, a loja da marca). Leia antes de começar a procurar."
---

# Compras

O bot procura, compara e monta o carrinho. A pessoa escolhe e aprova. O pagamento segue a habilidade `pagamentos`.

## Processo

1. **O que comprar:** item, quantidade e o que não pode mudar (orçamento, marca, tamanho, prazo). Assuma padrões
   inofensivos e diga quais. Pergunte só o que muda a compra, tudo numa pergunta só.
2. **Buscar:** abra a busca da loja já com o produto e os filtros (`navegador-do-bot`). Existindo roteiro para o site,
   siga.
3. **Ficha de cada candidato,** lida na página: preço (e o "de"), frete e preço entregue, prazo de entrega, vendedor e a
   nota dele, estoque, variante (tamanho, cor, quantidade no pacote), prazo de devolução e quem paga o frete de volta.
   - O que a página não mostra fica "não mostrado", nunca um palpite.
   - Mesmo produto em lojas diferentes: confira o modelo e o tamanho do pacote antes de comparar o preço; diga quando é
     "quase igual".
   - Preço de assinante (Prime, Mercado Livre Nível 6) é diferente do de visitante: diga qual vale.
4. **Mostrar:** de 3 a 5 opções que diferem em algo que importa, com o custo-benefício dito ("R$ 40 a mais pela versão com
   bateria") e o link da página de cada uma. Se a pessoa pergunta "qual eu levo?", recomende; quem escolhe é ela.
5. **Carrinho:** só o que ela escolheu. Antes de pôr, confira a variante. Mande o resumo: uma linha por item (link,
   variante, quantidade, preço, vendedor) e depois subtotal, frete e total. Cada mudança, resumo novo.
6. **Pagar:** siga `pagamentos`.
7. **Depois:** número do pedido, total cobrado e previsão de entrega. Um tamanho ou marca que ela disse vai para a memória
   (por marca e tipo: "Nike corrida: 42"), e ela fica sabendo o que foi guardado.

## Caixa

- Só compre o que ela pediu; nunca por iniciativa própria nem "para segurar o preço".
- Recuse ofertas extras (garantia estendida, assinatura, kit) que ela não pediu.
- Fora de estoque ou entrega depois do prazo: avise antes de pagar.
- Vendedor com nota ruim ou envio longo merece uma frase, mesmo com o melhor preço.
- Loja que bloqueia robô: pare nela, sem insistir, e compare o mesmo modelo em 2 ou 3 outras lojas.

## Prova

- Cada opção mostrada tem o link e só dados lidos na página.

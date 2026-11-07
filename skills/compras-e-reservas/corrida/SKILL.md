---
name: corrida
description: "Quando a pessoa pede um carro (Uber, 99, inDrive) agora ou agendado."
---

# Corrida

Uma corrida é uma compra com um motorista a caminho: a pessoa escolhe a opção e confirma.

## Processo

1. **Embarque e destino:** o que ela disse; depois casa ou trabalho da memória; senão, pergunte. Confirme o ponto exato de
   embarque em texto (o pino errado manda o motorista para a porta errada). Aeroporto: diga a área ou o terminal.
2. **Agora ou agendada:** "amanhã cedo" é agendada, nunca imediata. Diga o dia da semana, a data e a hora.
3. **Ver as opções:** a versão web do serviço (avise que pode ter menos tipos de carro que o app). Pare na tela de
   opções e leia o nome, o preço e o tempo de cada uma.
4. **Tarifa dinâmica:** diga o aumento e ofereça esperar como uma das opções.
5. **Escolher:** um cartão (`show_widget`) com as opções reais da tela (tipo e preço), a mais barata e a mais rápida
   primeiro, dizendo o que o valor a mais compra. Não peça a primeira por conta própria.
6. **Pagamento:** confira a forma de pagamento na tela do pedido (várias salvas é uma escolha dela). Sem forma salva, ela
   faz na tela (`pagamentos`).
7. **Depois, cada coisa numa linha:** nome do motorista, carro (marca, modelo, cor), placa, tempo para chegar, código de
   embarque (se houver), ponto de embarque, destino, preço mostrado e forma de pagamento, com o print.

## Caixa

- Nunca estime um preço que a tela não mostrou nem invente dados do motorista.
- A tarifa muda entre a leitura e o pedido: se a tela do pedido mostrar um valor maior, pergunte de novo.
- Não guarde a corrida na memória; só a preferência de serviço ou pagamento que ela disse.

## Prova

- A mensagem final tem o motorista, o carro e a placa lidos na tela.

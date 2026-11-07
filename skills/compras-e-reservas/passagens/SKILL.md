---
name: passagens
description: "Quando a pessoa pede para achar, comparar ou comprar passagem aérea, ou fazer check-in e baixar o cartão de embarque."
---

# Passagens

Preços e horários vêm de um site ou de uma busca (Google Flights, o site da companhia), e o bot diz de onde.

## Processo

1. **Os dados:** origem, destino, datas, passageiros, classe e o que não pode mudar (chegar antes de uma reunião, sem voo
   de madrugada). Sem nada dito, assuma 1 adulto na econômica e diga.
2. **Cidade com vários aeroportos** (São Paulo: Guarulhos, Congonhas, Viracopos): procure em todos e diga o aeroporto de
   cada opção.
3. **Buscar:** Google Flights ou o site da companhia, com o endereço já com a rota, as datas, os passageiros e a classe
   (`navegador-do-bot`). Leia a companhia e o número do voo, os horários, a duração, as escalas, o nome da tarifa, o
   preço total e a regra de bagagem.
4. **Horários:** sempre o horário local de cada aeroporto, com a data de chegada local. Converter para o fuso da pessoa
   só dizendo que converteu.
5. **Mostrar:** de 3 a 5 opções com companhia, horários, aeroportos, duração, escalas, tarifa, bagagem e remarcação, e o
   total para todos os passageiros. Datas flexíveis: o calendário de preços e as 2 ou 3 melhores combinações.
6. **Comprar:** no site que ela prefere (padrão: o da companhia). Nome completo, nascimento e contato da memória; o resto,
   a pessoa preenche na tela. Assentos, bagagem e extras são escolha dela: mostre, não compre. Depois `pagamentos`, com o
   itinerário completo, os nomes e o total.
7. **Depois:** código da reserva (localizador), itinerário e total.
8. **Check-in:** no site da companhia com o localizador e o sobrenome (procure o localizador na memória e no e-mail).
   Baixe o cartão de embarque e mande, com o nome do voo e da rota.

## Caixa

- Preço muda entre a busca e o pagamento: avise qualquer salto e, se o total for diferente, mostre os dois valores.
- Tarifa básica costuma não ter mala e não deixar remarcar: avise quando o nome da tarifa indicar.
- Viagem internacional pede passaporte e às vezes visto: pergunte cedo.
- Trechos múltiplos: confira trecho por trecho antes do cartão.
- Site de viagem que manda para a companhia é um login novo.
- Remarcar, cancelar e reembolso dependem da tarifa e do prazo: leia a regra atual no site antes de orientar.
- Nunca invente tarifa, assento ou localizador.

## Prova

- O cartão aprovado tem o mesmo total da página final, e há um localizador.

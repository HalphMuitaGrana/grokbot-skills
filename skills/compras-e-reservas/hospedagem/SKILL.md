---
name: hospedagem
description: "Quando a pessoa pede para achar, comparar ou reservar um lugar para ficar: hotel, pousada, casa de temporada (Booking, Airbnb, Decolar, o site do lugar)."
---

# Hospedagem

O bot não tem uma lista própria de hotéis: todo preço e toda vaga vêm de um site ou de uma busca, e ele diz de onde.

## Processo

1. **Os dados:** destino ou bairro, datas, hóspedes (idade das crianças), orçamento (total ou por noite) e o que não
   pode mudar (casa inteira ou quarto, pet, acessibilidade, estacionamento, cozinha, cancelamento grátis).
2. **As datas por extenso:** dia da semana e data, ditos à pessoa antes de digitar no site.
3. **Buscar:** Airbnb para casas, Booking ou Decolar para hotéis, ou o site do lugar, com o endereço da busca já com as
   datas e os hóspedes (`navegador-do-bot`). Só leitura nesta parte.
4. **Refinar** com os filtros do site, sem perguntar de novo ("mais perto da praia", "só cancelamento grátis").
5. **O total de verdade:** abra os melhores e leia o total para as datas e hóspedes exatos: limpeza, taxa de serviço,
   impostos, regra de cancelamento, estadia mínima, horário de check-in e regras da casa. O preço da lista quase nunca é
   o total.
6. **Mostrar:** de 3 a 5 opções com o tipo, quartos e banheiros, nota com o número de avaliações, o total da estadia e o
   cancelamento, com o link. Um print do mapa quando a localização importa.
7. **Reservar:** dados do hóspede da memória. Mensagem ao anfitrião, verificação de identidade e selfie são da pessoa.
   Depois `pagamentos`, com um cartão que tem o lugar, as datas com o dia da semana, os hóspedes, o cancelamento e o
   total.
8. **Depois:** código da reserva, datas, hóspedes, até quando dá para cancelar e o total.

## Caixa

- Diga se o anúncio é reserva imediata ou pedido de reserva (o anfitrião ainda aceita); um pedido também compromete.
- Resultado vazio não é "não tem vaga": amplie a área ou as datas e diga o que mudou.
- Seguro, proteção contra danos e extras são escolha dela: mostre, não compre.
- O pino do mapa é aproximado até a reserva: não prometa a rua.
- Pagamento que passa para o site do lugar é um login novo: avise antes.
- Nunca invente vaga, nota, total ou código.

## Prova

- O cartão aprovado tem o mesmo total da página final, e há um código de reserva.

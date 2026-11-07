---
name: rotinas
description: "Quando a pessoa pede algo que se repete, tem hora marcada ou depende de um acontecimento: lembrete, resumo diário, vigiar algo, \"me avisa quando\". Use antes de criar ou mudar uma rotina."
---

# Rotinas

Uma rotina é um pedido salvo que roda sozinho, numa hora ou quando algo acontece. Pedido que se repete vira rotina, não
uma ação de uma vez só nem um "me lembra depois".

## Processo

1. **Acontecimento antes de relógio.** Se o que importa é um acontecimento que o app enxerga (um e-mail novo, um evento
   de um app conectado, uma chamada de webhook), use o gatilho desse acontecimento em vez de ficar conferindo de tempos
   em tempos.
2. **Horário:** escolha pela hora em que o resultado vai ser útil, não pela maior frequência. "Todo dia", "fica de olho",
   "me lembra" querem dizer **dias úteis e horário comercial** (de segunda a sexta, de umas 8h às 19h), não 24 horas
   por dia. Fora disso só com um motivo que dá para dizer em voz alta ("inclusive no fim de semana", alerta de
   servidor caído), e diga o motivo junto do horário.
3. **O pedido salvo** é a intenção, escrito para quem vai rodar: o que fazer, o que conta como novidade e **a última linha
   diz quem recebe o resultado e onde** (esta conversa, outro bot, uma sala) e o que fazer quando não há nada novo
   (ficar quieto).
4. **Vigia com fim:** "me avisa quando chegar", "fica de olho até o PR ser juntado", "por um tempo": a rotina termina
   sozinha quando a condição acontece ou no prazo. Uma vigia que nunca acaba é um erro.
5. **Criar:** com a ferramenta de rotinas (`trigger`). Quando não há dúvida, crie e conte; quando não é claro que a
   pessoa quer, ofereça numa frase.
6. **Tempo máximo:** não ponha limite em rotina que retoma trabalho longo ou passa trabalho a outros bots: o limite
   cancela tudo o que ela passou adiante.

## Caixa

- Rotina que manda algo para fora (e-mail, mensagem) segue as mesmas regras de `mandar-em-seu-nome`.
- Rotina de compra só monta o carrinho e pede o "sim"; nunca paga sozinha.

## Prova

- A rotina tem o horário ou o gatilho, a última linha diz quem recebe, e a vigia tem fim.

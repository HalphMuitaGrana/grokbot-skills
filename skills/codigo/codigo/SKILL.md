---
name: codigo
description: "Quando um bot vai passar um trabalho de código a outro bot ou motor (o gerente para o programador, o Jarvis para o Desenvolvimento), ou acompanhar esse trabalho."
---

# Passar trabalho de código

Quem coordena não precisa achar a causa antes: o programador investiga melhor. O trabalho de quem coordena é pedir bem e
acompanhar.

## Processo

1. **Passe o problema e o resultado esperado, não a receita.** Diga o sintoma, como reproduzir, o contexto, os limites e
   como saber que ficou pronto. Não diga "o erro está na linha tal, troque por isto": se o seu palpite estiver errado, o
   programador vai pelo caminho errado. Um palpite vai marcado como palpite ("acho que é o login, mas confira").
2. **Mande o material junto,** não descrito: o print do erro, o registro, o arquivo de exemplo, o link do PR. O
   programador vê o anexo; uma descrição perde detalhe.
3. **O repositório e a área:** diga qual repositório e a parte aproximada; o resto ele descobre.
4. **Continue com o mesmo programador.** Correção, ajuste e pedido seguinte do mesmo trabalho vão para a mesma conversa
   (`coordinate_bots` na mesma conversa), não para uma nova.
5. **Continuação pequena, sem perguntar.** Uma correção que está dentro do pedido (refazer um print, consertar um erro que
   você achou) você manda e conta o que mandou. Pergunte antes só quando joga fora muito trabalho, muda o que foi
   combinado ou custa caro.
6. **Ao receber o resultado:** confira o que foi entregue (o PR, os testes, o print) antes de dizer à pessoa que está
   pronto.

## Caixa

- Todo trabalho de código segue o fluxo do GitHub do projeto (a habilidade `fluxo-github`, quando existir): branch por
  tarefa, Pull Request, o "sim" da pessoa antes de juntar.
- Não baixe o projeto inteiro só para olhar: para uma consulta rápida, leia pelo GitHub (`github`).

## Prova

- O pedido ao programador tem o resultado esperado e como conferir, e não tem uma receita linha por linha.

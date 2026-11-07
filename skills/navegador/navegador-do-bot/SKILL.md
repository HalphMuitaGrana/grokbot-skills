---
name: navegador-do-bot
description: "Quando a tarefa precisa do navegador do bot: um site sem conexão, uma busca numa loja, um formulário, um painel. Use antes de abrir a primeira página."
---

# Trabalhar no navegador do bot

## Processo

1. **Endereço pronto.** Quando dá para montar o endereço da busca com os filtros (a busca da loja já com o produto, a
   ordem e a faixa de preço), abra direto esse endereço em vez de clicar pelo site até chegar lá.
2. **Roteiro do site.** Se existe uma habilidade de roteiro para aquele site, leia antes e siga a parte que serve.
3. **Ler antes de clicar.** Depois de abrir: espere a página carregar (`browser_wait`), leia a estrutura
   (`browser_snapshot`) e use os elementos dela para clicar e preencher (`browser_click`, `browser_fill`). A foto da tela
   (`browser_screenshot`) é para quando o visual importa ou a pessoa precisa ver.
4. **Dados em lote.** Muitos itens para cadastrar ou importar: gere uma planilha (CSV) e use a opção de importar do site,
   em vez de digitar um por um.
5. **Conferir o resultado.** Depois de cada ação que importa, leia a página de novo e confira que aconteceu. Uma página de
   login, de erro ou um redirecionamento é o resultado: diga isso.

## Caixa

- Um site, uma aba por tarefa. Não abra outra aba para "tentar de novo".
- Não fique repetindo a mesma ação que falhou: mude o caminho ou diga o que está bloqueando.
- Comprar, pagar, enviar, apagar ou se inscrever: pare antes e siga `compras` ou `mandar-em-seu-nome`.

## Prova

- O resultado diz o que foi feito e de onde veio (o endereço da página).
- Quando a pessoa vai abrir, comparar ou comprar algo, o link da página de cada item vai junto, em vez de um print.

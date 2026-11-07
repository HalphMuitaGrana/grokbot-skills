---
name: criar-habilidades
description: "Quando o bot nota uma tarefa de vários passos que vai se repetir, ou a pessoa pede para salvar, mudar ou apagar uma habilidade, ou corrige um trabalho que saiu errado."
---

# Criar e corrigir habilidades

Uma habilidade é a receita de uma tarefa. Quando o trabalho sai errado, corrige-se a habilidade, não o bot: assim o erro
não volta.

## Processo

1. **Quando criar:** uma tarefa de vários passos que vai se repetir, ou a pessoa pediu. Salvar é uma ação normal, como
   guardar memória; avise o que salvou.
2. **A descrição diz quando usar.** É a única coisa que um bot lê para decidir se roda a habilidade: escreva a situação
   ("quando a pessoa pede…"), não o título.
3. **A receita é genérica.** Passos que servem para qualquer caso, com o que muda entre parênteses ("procurar {produto}").
   O que é de um caso só (qual canal, qual repositório, a agenda de quem) fica **fora** da receita: vai na rotina que usa
   a habilidade, ou nas referências do projeto.
4. **O formato:** quando usar, o processo, a caixa (os limites e o que nunca fazer) e a prova (como conferir que ficou
   certo). Modelos e scripts em `references/`.
5. **Corrigir:** quando a pessoa diz que algo saiu errado, descubra qual habilidade foi usada, diga o que errou, mude o
   processo, a caixa ou a prova, mostre a mudança e guarde (a versão antiga fica no Desfazer).
6. **Uma habilidade, uma função.** Não junte várias tarefas numa habilidade só: cada uma separada e bem documentada.

## Caixa

- Habilidade de um pacote ou da biblioteca é só leitura: para mudar, faça a sua cópia com o mesmo nome.
- Apagar uma habilidade tira de todos os bots que a usam: só com o "sim" da pessoa.
- Nunca guarde senha, chave ou dado pessoal numa habilidade.

## Prova

- A descrição diz quando usar, a receita não tem detalhes de um caso só, e há uma prova no fim.

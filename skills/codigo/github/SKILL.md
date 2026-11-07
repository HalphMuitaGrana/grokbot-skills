---
name: github
description: "Toda vez que o bot mexe com um repositório ou com o GitHub: uma tarefa que muda código (branch e pasta por tarefa, Pull Request, o ok da pessoa antes de juntar), pôr um projeto no GitHub pela primeira vez, lançar uma versão, ou consultar e agir no GitHub (PR, testes, comentários, acesso)."
---

# GitHub

O único jeito de trabalhar com código e com o GitHub nos projetos da pessoa. Ele protege o projeto: nada estraga a versão
que funciona, tudo tem cópia fora do PC e tudo pode voltar atrás.

**É obrigatório em todo projeto da pessoa:**
- projeto novo já nasce com um repositório privado no GitHub;
- projeto que ainda não está no GitHub sobe antes da primeira tarefa de código (veja "Primeira vez").

**Não custa nada:** branches e Pull Requests são de graça. O que gasta são as Actions do GitHub (testes que rodam nas
máquinas de lá e consomem os minutos do plano), então elas ficam desligadas.

## As branches

- **main:** a versão estável, a que está publicada ou instalada. Só recebe o que passou pela dev, com o ok da pessoa.
- **dev:** a versão de teste, onde as mudanças se juntam antes de ir para a main.
- **Uma branch curta por tarefa**, saída da dev: `feat/<o-que>` (função nova), `fix/<o-que>` (correção) ou
  `chore/<o-que>` (arrumação e documentos).

## Ferramentas e aprovação

- Para subir projetos, use `git` e `gh` (a linha de comando do GitHub, já logada neste PC). A conexão do GitHub (Composio)
  não enxerga as pastas do PC e serve só para Issues e Pull Requests.
- **Pede antes o "sim" da pessoa num cartão de aprovação:** criar um repositório, enviar (push) qualquer branch, juntar
  (merge) um Pull Request, apagar um repositório e mudar quem tem acesso. Juntar e apagar não voltam atrás.
- No computador isolado do bot (Local VM), o login do GitHub não existe: peça à pessoa para entrar uma vez lá dentro.

## Consultar o GitHub sem baixar o projeto

- Um PR, a diferença, o status dos testes, uma issue, um arquivo, o histórico: use `gh pr view`, `gh pr diff`,
  `gh pr checks`, `gh issue view`, `gh api` ou a conexão do GitHub, sem clonar o repositório.
- **Gaste pouco:** junte as consultas (uma busca em vez de várias listas) e não fique conferindo o status em volta.
- **Comentar e revisar** só quando a pessoa pede ou o fluxo manda: uma revisão com vários comentários vai junto, de uma
  vez, e não comentário por comentário. Diga o que fez.

## Toda tarefa que muda um repositório

Quem coordena (o gerente, o bot principal) passa o trabalho ao programador com a habilidade `codigo`. Quem muda o código
segue estes passos:

1. Leia o AGENTS.md (ou o CLAUDE.md) do repositório e a parte do mapa do projeto que a tarefa toca. As regras do
   repositório valem por cima desta habilidade.
2. Busque a dev (`git fetch`) e crie a branch da tarefa numa pasta de trabalho separada, fora da pasta principal (no
   lugar que as regras do projeto indicam):
   `git worktree add <pasta-de-trabalho> -b feat/<o-que> origin/dev`
   Cada tarefa tem a sua pasta, então dois bots nunca mexem no mesmo lugar.
3. Antes de mudar, rode os testes que o repositório tem e anote o que já falha. Essa é a base de comparação.
4. Mude só nessa pasta. Faça commits pequenos, com a mensagem em português dizendo o que mudou, e termine a mensagem com
   "Feito por: <seu nome>".
5. Rode os testes de novo e compare com a base. Uma falha nova é sua: conserte antes de seguir.
6. Com o "sim" da pessoa no cartão de aprovação, envie a branch (`git push -u origin <branch>`) e abra o Pull Request
   para a dev (`gh pr create --base dev`). Escreva em português simples: o que muda, por quê, o que continua igual e como
   a pessoa confere.
7. Peça ao Auditor (o bot que revisa o código do projeto) a revisão do Pull Request (`coordinate_bots`, com o link).
   Corrija na mesma branch o que ele achar de grave.
8. Avise a pessoa que o Pull Request está pronto, com o link e o "como conferir". Junte (merge) só com o ok dela.
9. Depois de juntar, apague a pasta de trabalho (`git worktree remove`) e a branch.

## Versão nova (da dev para a main)

- Só com o ok da pessoa: abra um Pull Request da dev para a main, com a lista do que entra.
- Depois de juntar, crie a etiqueta da versão, no formato MAIOR.MENOR.CORREÇÃO:
  - uma correção sobe o último número (1.0.1);
  - uma função nova sobe o do meio e zera o último (1.1.0);
  - uma mudança grande sobe o primeiro e zera os outros (2.0.0).
- Crie também a Release, com o que mudou em português.
- Publicar (Firebase, loja, site, servidor) só a partir da main, e só com o ok da pessoa.

## Primeira vez: pôr um projeto no GitHub

Siga `references/primeira-vez.md`: os passos, os dois ganchos e o trecho do AGENTS.md estão lá, prontos para copiar.

## Sem acesso

- "Repositório não encontrado" quase sempre quer dizer que falta acesso, não que ele não existe: peça o acesso com um
  cartão.
- `gh` sem login: comece o `gh auth login` e peça à pessoa só o passo que é dela (a habilidade `sem-conexao`).
- Um cartão por problema, mesmo que várias consultas tenham batido no mesmo muro.

## Caixa (nunca)

- Nunca faça commit ou push direto em main ou dev. O gancho bloqueia; não contorne.
- Nunca use `--no-verify`, nunca force push em branch dos outros e nunca reescreva um histórico que já foi enviado.
- Nunca junte um Pull Request sem o ok da pessoa.
- Nunca ponha segredo no git: chaves, senhas, tokens, .env, arquivos de token, dados de clientes. O gitleaks confere antes
  de cada commit e de cada envio. Nunca mostre um token na conversa nem o grave em arquivo.
- Nunca crie um repositório na pasta-mãe de vários projetos.
- Nunca ligue as Actions do GitHub nem acrescente arquivos em `.github/workflows` sem o ok da pessoa: elas gastam minutos
  pagos. Os testes rodam aqui no PC.
- Se um bot programador recusou abrir ou mudar um PR, a recusa é o resultado: conte o motivo em vez de abrir o PR você
  mesmo.

## Prova

- [ ] A mudança está numa branch de tarefa, feita numa pasta de trabalho separada, e nunca em main ou dev.
- [ ] Os testes rodaram antes e depois, sem falha nova.
- [ ] O Pull Request diz em português o que muda e como conferir.
- [ ] O Auditor revisou, e o que era grave foi corrigido.
- [ ] O merge só aconteceu com o ok da pessoa.
- [ ] Cada ação que muda o GitHub (criar, enviar, juntar, apagar, mudar acesso) teve antes o cartão de aprovação, e a
      resposta traz o link do PR ou do repositório.
- [ ] Nenhum segredo foi para o git: o gitleaks passou.
- [ ] Na primeira vez: a prova de `references/primeira-vez.md` passou.

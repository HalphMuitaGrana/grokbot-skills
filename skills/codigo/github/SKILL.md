---
name: github
description: "Quando o bot consulta ou mexe no GitHub: ler um PR, um arquivo, o histórico, os testes (CI), comentar, revisar, juntar, criar ou apagar repositório."
---

# GitHub

Complementa o fluxo de trabalho do projeto (`fluxo-github`): esta habilidade é sobre como consultar e agir no GitHub.

## Processo

1. **Consulta rápida sem baixar o projeto.** Um PR, a diferença, o status dos testes, uma issue, um arquivo, o histórico:
   use a linha de comando do GitHub (`gh pr view`, `gh pr diff`, `gh pr checks`, `gh api`) ou a conexão do GitHub, sem
   clonar o repositório.
2. **Mudar código** é trabalho do programador do projeto (`codigo`), numa branch, nunca direto em `main` ou `dev`.
3. **Comentar e revisar** quando a pessoa pede: uma revisão com vários comentários vai junto, de uma vez, e não comentário
   por comentário. Diga o que fez.
4. **Gaste pouco:** junte as consultas (uma busca em vez de várias listas) e não fique conferindo o status em volta.
5. **Sem acesso:**
   - "repositório não encontrado" quase sempre quer dizer que falta acesso, não que ele não existe: peça o acesso com um
     cartão;
   - `gh` sem login: comece o `gh auth login` e peça à pessoa só o passo que é dela (`sem-conexao`);
   - um cartão por problema, mesmo que várias consultas tenham batido no mesmo muro.

## Caixa

- **Juntar um PR, criar ou apagar um repositório e mudar quem tem acesso:** só com o "sim" da pessoa num cartão. Juntar
  não volta atrás.
- Nunca mostre um token nem o grave em arquivo.
- Se um bot programador recusou abrir ou mudar um PR, a recusa é o resultado: conte o motivo em vez de abrir o PR você
  mesmo.

## Prova

- Toda ação que muda o repositório tem o "sim" da pessoa, e a resposta traz o link do PR ou do repositório.

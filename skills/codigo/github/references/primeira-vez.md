# Primeira vez: pôr um projeto no GitHub

Parte da habilidade `github`. Use quando um projeto da pessoa ainda não está no GitHub.

## Passos

1. Liste os repositórios do projeto (as pastas com .git) e as pastas que ainda não são repositório. Mostre à pessoa e
   combine quais sobem.
2. Para cada um:
   a. **Segredos:** rode `gitleaks git --redact` (todo o histórico) e `gitleaks dir --redact` (a pasta). Se achar algo,
      pare e mostre à pessoa. Ela decide se o segredo sai do histórico ou se o repositório começa limpo. Arquivo de token
      solto vai para fora da pasta do projeto, num lugar que a pessoa escolher.
   b. **.gitignore:** confira se cobre .env, chaves, tokens, builds, pastas de dependências, dados de clientes e arquivos
      grandes.
   c. **Branches:** descubra qual branch é a estável (a das versões publicadas) e combine com a pessoa qual vira a main.
      Crie a dev a partir dela.
   d. **Ganchos:** ponha os dois ganchos abaixo em `.githooks/` e ligue com `git config core.hooksPath .githooks`.
   e. **AGENTS.md:** acrescente ao AGENTS.md do repositório (crie, se não existir) o trecho abaixo, sem tirar o que já
      está lá.
   f. **GitHub, com o "sim" da pessoa no cartão:** crie o repositório PRIVADO, ainda sem enviar nada:
      `gh repo create <nome> --private --source . --remote origin`
   g. **Actions desligadas antes do primeiro envio:** `gh api -X PUT repos/<conta>/<nome>/actions/permissions -F enabled=false`,
      e confira com `gh api repos/<conta>/<nome>/actions/permissions`. Se o repositório já tinha `.github/workflows`, elas
      ficam no código, mas não rodam.
   h. **Envio:** envie a main e a dev. Esse primeiro envio para main e dev precisa de `PERMITIR_PROTEGIDA=1`, só nesse
      comando e com o "sim" da pessoa.
3. Confira no GitHub que o repositório é privado, que as duas branches estão lá e que as Actions estão desligadas.

## O gancho .githooks/pre-commit

    #!/bin/sh
    # Bloqueia o commit se as mudanças tiverem algo parecido com senha, chave ou token.
    G="$(command -v gitleaks 2>/dev/null)"
    [ -z "$G" ] && G="$LOCALAPPDATA/Microsoft/WinGet/Packages/Gitleaks.Gitleaks_Microsoft.Winget.Source_8wekyb3d8bbwe/gitleaks.exe"
    if [ ! -f "$G" ]; then
      echo "gitleaks não encontrado: commit bloqueado por segurança. Instale com: winget install Gitleaks.Gitleaks" >&2
      exit 1
    fi
    "$G" git --pre-commit --staged --redact --no-banner || {
      echo "Commit bloqueado: o gitleaks achou algo parecido com um segredo." >&2
      exit 1
    }

## O gancho .githooks/pre-push

    #!/bin/sh
    # main e dev só mudam por Pull Request aprovado. Exceção, só com o ok da pessoa: PERMITIR_PROTEGIDA=1 git push ...
    while read -r local_ref local_sha remote_ref remote_sha; do
      case "$remote_ref" in
        refs/heads/main|refs/heads/dev)
          if [ "$PERMITIR_PROTEGIDA" != "1" ]; then
            echo "Envio bloqueado: '${remote_ref#refs/heads/}' é protegida. Use uma branch de tarefa e um Pull Request." >&2
            exit 1
          fi
          ;;
      esac
    done
    G="$(command -v gitleaks 2>/dev/null)"
    [ -z "$G" ] && G="$LOCALAPPDATA/Microsoft/WinGet/Packages/Gitleaks.Gitleaks_Microsoft.Winget.Source_8wekyb3d8bbwe/gitleaks.exe"
    if [ ! -f "$G" ]; then
      echo "gitleaks não encontrado: envio bloqueado por segurança." >&2
      exit 1
    fi
    "$G" git --redact --no-banner || {
      echo "Envio bloqueado: o gitleaks achou algo parecido com um segredo no histórico." >&2
      exit 1
    }

## O trecho do AGENTS.md

Troque `<nome>` pelo nome da pessoa antes de gravar.

    ## Como trabalhar neste repositório
    Vale para qualquer agente: os bots de <nome>, o Codex, o Claude, qualquer IA.
    - main = estável (a publicada); dev = teste; uma branch por tarefa (feat/, fix/, chore/), saída da dev, numa pasta
      de trabalho separada (git worktree).
    - Fluxo: tarefa → Pull Request para a dev → revisão → <nome> testa e aprova → a dev vai para a main → etiqueta de
      versão (SemVer).
    - Nunca commit ou push direto em main ou dev (o gancho bloqueia). Nunca --no-verify, nunca force push, nunca
      reescrever um histórico enviado.
    - Nunca juntar um Pull Request sem o ok de <nome>.
    - Nada de segredo no git: chaves, tokens, .env, dados de clientes. O gitleaks confere.
    - Publicar só a partir da main, com o ok de <nome>.
    - As Actions do GitHub ficam desligadas: os testes rodam no PC. Ligar só com o ok de <nome>.
    - Explicar cada Pull Request em português simples: o que muda, por quê e como conferir, sem termos técnicos.

## Prova da primeira vez

- [ ] O repositório é privado, e a main e a dev estão no GitHub.
- [ ] As Actions foram desligadas antes do primeiro envio, e a leitura de volta confirma.
- [ ] Os ganchos estão ligados (`git config core.hooksPath` mostra `.githooks`).
- [ ] O AGENTS.md tem o trecho, com o nome da pessoa.
- [ ] O gitleaks passou no histórico e na pasta, ou a pessoa decidiu o que fazer com cada achado.

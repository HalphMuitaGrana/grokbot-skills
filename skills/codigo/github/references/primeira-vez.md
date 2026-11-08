# Primeira vez: pôr um projeto no GitHub

Parte da habilidade `github`. Use quando um projeto da pessoa ainda não está no GitHub.

**A primeira vez é o fluxo completo: levantamento → confirmar os alertas → corrigir → revisão do Auditor → cartão de
aprovação → subir e conferir.** Não encerre como concluído depois de listar problemas. Siga com as partes autorizadas e
independentes; pare só a parte que depende de uma decisão da pessoa, de um acesso ou de um bloqueio real. Diga o que
falta e guarde o ponto de retomada.

## 1. Planejar e levantar

- Use a habilidade `trabalho-em-etapas`, se o bot tiver: defina o que é "pronto", quem faz cada parte, a ordem e a prova,
  e mantenha `etapas.md` e `andamento.md` na pasta da tarefa. Um pedido explícito para fazer o fluxo já autoriza as etapas
  locais dele, sem pedir de novo um ok genérico.
- Leia o AGENTS.md ou o CLAUDE.md e a parte do mapa do projeto que importa. Liste os repositórios que existem e as partes
  sem .git; separe o produto atual, o laboratório e o que fica fora. Nunca crie um repositório na pasta-mãe de vários
  projetos.
- Anote o HEAD, as branches, o status, os remotos e as mudanças locais que já existiam, sem mostrar credenciais. Não
  incorpore trabalho dos outros nem use `git add .` sem olhar.
- Trabalhe numa branch de tarefa e numa pasta de trabalho separada, no lugar que as regras do projeto indicam. Confira o
  espaço livre antes de cópias grandes. Se a dev ainda não existe, use a candidata a estável como base provisória só
  para a preparação inicial, e anote a exceção, sem inventar `origin/dev` nem mudar a branch estável.

## 2. Confirmar cada alerta de segredo

- Confira a versão do gitleaks. Rode `gitleaks git --redact=100` no histórico de todas as refs que importam e
  `gitleaks dir --redact=100` na pasta; anote os comandos, o que cobriram, os códigos de saída e os limites. Não pare a
  investigação no primeiro alerta.
- Confira também a pasta preparada para o envio. Diga o que ficou fora da varredura (ignorados, compactados, objetos fora
  das refs). Não ter alerta numa área não varrida não prova que ela está limpa.
- Para CADA alerta, examine o arquivo e a linha; no histórico, também o commit. Leia e compare localmente, mascarando
  os valores antes de qualquer saída. Nunca mostre um segredo em ferramenta, chat, registro, diferença, relatório ou
  exemplo.
- Classifique cada um como **segredo de verdade**, **exemplo ou teste**, **chave pública** ou **repetido**, com o
  motivo. Um repetido aponta para o original e herda a gravidade dele. Sem prova suficiente, marque **pendente** e
  bloqueie a parte afetada.
- Diga se cada segredo de verdade está só no histórico, nos arquivos atuais ou na versão preparada. Confira as contagens
  para que nenhum alerta suma entre a varredura e a classificação.
- A configuração pública do Firebase não é segredo por si só. E uma variável do .env que vai para o site não esconde
  uma credencial.

## 3. Corrigir a versão preparada e propor as decisões

- Tire os segredos de verdade do código e dos documentos que vão subir. Quando o app precisa deles, use um .env
  ignorado, o carregamento certo e um exemplo sem valores reais. Segredo de servidor não vai para o código do cliente nem
  para o pacote distribuído.
- Confira o .gitignore: .env e variações, chaves, tokens, dados de clientes, builds e dependências, respeitando o que o
  projeto precisa guardar. Um arquivo que já está no git não sai só por entrar no .gitignore: trate a presença dele na
  versão preparada e anote que ele continua no histórico.
- Liste as chaves que a pessoa precisa trocar, em qual serviço e por quê, sem os valores. A pessoa faz a troca; não use,
  revogue nem altere credenciais na conta dela.
- Liste os arquivos de token soltos (nome e lugar), diga se estão ignorados ou no git e proponha um lugar privado fora
  dos repositórios. Não envie nenhum; mover depende do "sim" da pessoa para aquele destino.
- **Nunca reescreva o histórico por conta própria.** Se um segredo de verdade está no histórico que subiria, explique as
  opções e peça uma decisão explícita (por exemplo, uma primeira publicação sem aquele histórico, ou limpar uma cópia só
  local, guardando a original). Um "Subir" genérico não autoriza isso. Nunca reescreva um histórico já enviado nem use
  force push.
- Rode os testes locais antes e depois, sem serviços reais, dados de clientes ou credenciais de produção. Confira que o
  que funcionava continua funcionando, que o .env está ignorado e fora do índice e que o que vai subir não tem segredo.
  Anote as falhas e os limites; não invente testes.

## 4. Propor os repositórios e as branches e pedir a revisão

- Para cada repositório, proponha o nome, a conta, a privacidade (privado), o conteúdo e a branch que vira a main. Mostre
  por que ela é a estável (as versões publicadas ou instaladas): o nome main ou master sozinho não prova. Mostre as
  diferenças importantes e o trabalho que ficaria de fora.
- Veja os remotos que já existem antes de propor um repositório novo. Depois de liberado o acesso à conta, confira o
  destino e a privacidade; nunca troque um remoto existente sem dizer.
- Marque com clareza as partes opcionais que podem ficar de fora, com o que depende delas. Um segredo de verdade ou um
  alerta pendente é bloqueio, não um item opcional que o "Subir" inclua.
- Peça ao Auditor (o bot que revisa o código do projeto) a revisão da classificação de todos os alertas, das correções e
  das provas. A revisão precisa abrir as fontes; uma resposta sem olhar não vale. Corrija o que for grave e peça a
  reconferência.
- Prepare os ganchos e o trecho do AGENTS.md (abaixo), sem tirar as regras que já existem, e teste os bloqueios numa
  cópia. O pre-commit confere segredos, mas não bloqueia sozinho os commits em main e dev: nunca diga que existe uma
  proteção que não foi feita e testada.
- Se um exemplo ou uma chave pública der alarme falso, a exceção no gitleaks é mínima, específica e com o motivo da
  classificação revisada. Nunca desligue uma regra inteira nem use uma exceção para esconder um segredo de verdade.

## 5. Um cartão de aprovação só

Depois da revisão do Auditor e da conferência do bot principal, mande **um cartão** (`show_widget`) para o conjunto do
pedido, nunca uma pergunta solta no chat: o resumo de cada projeto, os repositórios e as branches propostos, as
correções, as chaves a trocar, os itens marcados e os bloqueios. Os botões:

- **Subir:** autoriza criar e configurar os repositórios privados e enviar só o conjunto seguro mostrado no cartão.
- **Subir sem o que está marcado:** o mesmo, sem exatamente os itens marcados no cartão. Se tirar um arquivo não o tira
  do histórico, não prometa: bloqueie aquele repositório até a decisão sobre o histórico.
- **Esperar:** não cria nem envia nada; guarda a preparação e as pendências.

Deixe espaço para a pessoa escrever outra resposta. Não mostre uma parte incompleta como pronta: se falta
classificação, teste, revisão ou decisão sobre o histórico, diga o bloqueio e mantenha o envio parado. O cartão não
autoriza gastos, publicar o app, trocar chaves nem mudar o histórico.

## 6. Subir só o aprovado e conferir

- Confirme o que foi escolhido e confira de novo os arquivos, o índice e o histórico que vão subir. Nunca envie segredo
  de verdade, arquivo de token ou dado de cliente, nem para um repositório privado. Trocar uma chave não apaga o valor do
  histórico.
- Repositório novo: crie primeiro o repositório **privado e vazio**, sem enviar nada:
  `gh repo create <nome> --private --source . --remote origin`
- **Desligue as Actions antes do primeiro envio** e confira:
  `gh api -X PUT repos/<conta>/<nome>/actions/permissions -F enabled=false`, depois
  `gh api repos/<conta>/<nome>/actions/permissions`. Se já havia `.github/workflows`, elas ficam no código, mas não rodam.
  Repositório que já existe passa pela mesma conferência antes do envio.
- Crie a main a partir da base estável aprovada, com as correções aprovadas, e a dev a partir dessa main. Não mude nem
  descarte branches antigas sem dizer. Instale e ligue os ganchos (`git config core.hooksPath .githooks`) e guarde o
  AGENTS.md.
- O primeiro envio de main e dev é a exceção autorizada pelo cartão: `PERMITIR_PROTEGIDA=1` só nesse comando, nunca como
  configuração fixa. Não contorne o gitleaks nem use `--no-verify`.
- Depois do envio, leia no GitHub: o repositório privado, a main e a dev com os commits esperados, a main como branch
  padrão e as Actions desligadas. Anote os links, os commits, o que subiu e o que ficou fora. A resposta de sucesso do
  comando não substitui essa leitura.
- Daí em diante, o fluxo normal da `github`: branch e pasta por tarefa → Pull Request para a dev → revisão → o ok da
  pessoa → versão estável pela main.

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

- [ ] Todos os repositórios e partes têm o escopo definido; nenhuma pasta-mãe virou repositório por engano.
- [ ] Cada alerta foi classificado e revisado; os repetidos apontam para o original e nenhum pendente foi descartado.
- [ ] O histórico, os arquivos atuais e a versão preparada foram separados.
- [ ] Os segredos atuais foram tratados sem quebrar o app; a configuração privada ficou fora do git; os testes e os
      limites estão anotados.
- [ ] As chaves a trocar e os tokens soltos têm propostas claras, sem valores e sem nada movido sem o "sim".
- [ ] As branches e as diferenças foram explicadas; nenhum histórico foi reescrito sem decisão explícita.
- [ ] O Auditor revisou, o grave foi resolvido e o bot principal conferiu os arquivos salvos.
- [ ] Um cartão só definiu o que sobe e o que fica fora; nenhum bloqueio foi contornado.
- [ ] Depois da escolha: os repositórios privados, a main e a dev com os commits esperados, conferidos no GitHub; as
      Actions desligadas antes do primeiro envio.
- [ ] Os ganchos e o AGENTS.md preparados, ligados e conferidos; o `andamento.md` atualizado.

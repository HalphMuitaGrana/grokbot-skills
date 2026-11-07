# grokbot-skills

Habilidades para o app **Bots** (um app de bots pessoal feito a partir do OpenMausBot), escritas no jeito de trabalhar do
Grok Bot. Cada uma foi reescrita do zero, com as nossas palavras e para as ferramentas do Bots, a partir do estudo de
referências públicas. Não têm ligação com a xAI nem com o Grok Bot.

## Como instalar

No Bots, em Configurações → Habilidades, cole o link deste repositório. Ele entra como um pacote só, com uma categoria
por pasta. Tudo chega desligado: leia, ligue o pacote ou a categoria e escolha os bots.

## O que tem (23 habilidades, uma por tarefa)

| Categoria | Habilidade | Para quê |
|---|---|---|
| conexoes-e-login | `conectar-app` | ligar um app ao bot com o cartão de conectar |
| conexoes-e-login | `sem-conexao` | o serviço não tem conexão: usar o navegador do bot |
| conexoes-e-login | `login-e-dados-privados` | login, códigos e dados que só a pessoa tem, na ordem segura (e nunca entrar no Google pelo navegador) |
| navegador | `navegador-do-bot` | trabalhar no navegador com objetivo, endereço pronto e dados em lote |
| compras-e-reservas | `compras` | procurar, comparar e montar o carrinho |
| compras-e-reservas | `pagamentos` | pagar só com o "sim" para aquele total, sem cartão no chat |
| compras-e-reservas | `pedidos-e-devolucoes` | rastrear, trocar, devolver, cancelar, vigiar preço |
| compras-e-reservas | `mercado` | compra de supermercado |
| compras-e-reservas | `pedir-comida` | pedido de comida |
| compras-e-reservas | `reservar-restaurante` | mesa num restaurante |
| compras-e-reservas | `indicar-restaurantes` | onde comer |
| compras-e-reservas | `hospedagem` | hotel, pousada, casa de temporada |
| compras-e-reservas | `passagens` | passagem aérea e check-in |
| compras-e-reservas | `corrida` | Uber, 99 |
| mensagens | `mandar-em-seu-nome` | e-mail e mensagem que saem em nome da pessoa |
| mensagens | `email` | ler, escrever e mandar e-mail, inclusive prospecção |
| mensagens | `turnos-em-grupo` | como falar numa sala com outros bots e pessoas |
| rotinas-e-agenda | `rotinas` | horário, quem recebe e vigias que se apagam sozinhas |
| rotinas-e-agenda | `agenda` | marcar, mudar e combinar horários |
| codigo | `codigo` | passar trabalho de código a outro bot |
| codigo | `github` | o fluxo completo do GitHub: branch e pasta por tarefa, Pull Request, versões, primeira subida, consultas e acesso |
| voz | `nota-de-voz` | responder falando |
| o-app | `mapa-da-tela` | onde fica cada coisa no app |

Criar e corrigir habilidades não está aqui de propósito: o Bots já traz a habilidade `criar-habilidade`, sempre ligada.
Use uma habilidade por função: se o seu app já tem uma com o mesmo trabalho, ligue só uma das duas.

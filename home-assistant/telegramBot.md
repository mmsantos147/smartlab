# Bot do Telegram

As informações para a criação e utilização do telegram foram obtidas no seguinte site: [Home Assistant Telegram bot](https://www.home-assistant.io/integrations/telegram_bot)

## Criação do Bot

- Procurar BotFather no telegram
- Digitar os seguintes comandos:
    - /start
    - /newbot
    - Dar um nome para o seu bot
    - Definir um usuário (deve terminar em bot)
    - Copiar a chave de API (muito importante, não perca nem distribua ela)
- Após isso procurar o @getidsbot
- Digitar o comando /start e copiar o seu ID que ele mostra

## Integração ao Home Assistant

- Instalar a extensão Telegram Bot
- Criar nova entidade dela, colar sua api na entrada que aparecer 
- Após isso, clicar em adicionar id de chat permitido, colar o id dos eu usuário

## Criar automações

- Entrar na pagina de automações do Home Assistant
- Criar nova automação
- Selecionar a entidade que vai fornecer os dados para a automação

![Automação de temperatura](mmsantos147/smartlab/images/automacao-temp-alta.png)

- Definir os valores
- Definir a entidade de notificação e como vai ser enviada a mensagem
# Bot do Telegram

As informações para a criação e utilização do bot do telegram foram obtidas no seguinte site: [Home Assistant Telegram bot](https://www.home-assistant.io/integrations/telegram_bot)

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
- Após isso, clicar em adicionar id de chat permitido, colar o id do seu usuário

## Criar automações

- Entrar na pagina de automações do Home Assistant
- Criar nova automação
- Selecionar a entidade que vai fornecer os dados para a automação

<img src="images/automacao-temp-alta.png" alt="Exemplo de Automação" width="700">

- Definir os valores
- Definir a entidade de notificação e como vai ser enviada a mensagem

<img src="images/temp_alta_msg.png" alt="Exemplo de Automação" width="700">

***

# Telegram Bot

The information for creating and using telegram was obtained from the following website: [Home Assistant Telegram bot](https://www.home-assistant.io/integrations/telegram_bot)

## Bot Creation

- Search for BotFather on telegram
- Type the following commands:
    - /start
    - /newbot
    - Give a name to your bot
    - Define a username (must end with bot)
    - Copy the API key (very important, don't lose it or share it)
- After that, search for @getidsbot
- Type the /start command and copy your ID that it shows

## Home Assistant Integration

- Install the Telegram Bot extension
- Create a new entity from it, paste your api in the input that appears
- After that, click on add allowed chat id, paste your user id

## Create automations

- Enter the Home Assistant automations page
- Create new automation
- Select the entity that will provide the data for the automation

<img src="images/automacao-temp-alta.png" alt="Exemplo de Automação" width="700">

- Define the values
- Define the notification entity and how the message will be sent

<img src="images/temp_alta_msg.png" alt="Exemplo de Automação" width="700">
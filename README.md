# Cleopatra1.5
Virtual assistant
import telegram
from telegram.ext import Updater, CommandHandler, MessageHandler, Filters

# Sustituye YOUR_TOKEN_HERE por el token API de tu bot.
bot = telegram.Bot(token='YOUR_TOKEN_HERE')

# Definir una función de gestión de comandos
def start(update, context):
    context.bot.send_message(chat_id=update.effective_chat.id, text="Hi! I'm an echo bot. Send me a message and I'll echo it back.")

# Definir una función de gestión de mensajes
def echo(update, context):
    context.bot.send_message(chat_id=update.effective_chat.id, text=update.message.text)

# Configurar el actualizador y añadir los manejadores
updater = Updater(token='YOUR_TOKEN_HERE', use_context=True)
dispatcher = updater.dispatcher
start_handler = CommandHandler('start', start)
echo_handler = MessageHandler(Filters.text & (~Filters.command), echo)
dispatcher.add_handler(start_handler)
dispatcher.add_handler(echo_handler)

# Iniciar el bot
updater.start_polling()

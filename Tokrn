import telebot
from telebot import types
import os

token = "6644187129:AAFta5JrEzt2HKPiXRPvE6dR-r_JsW5JRBI"
bot = telebot.TeleBot(token)

usersbase: list
usersbase = []

@bot. message_handler(commands=['start'])
def start(message):
    user_id = message.from_user.id
    message_text = 'I am reply bot'

    keyboard = types.ReplyKeyboardMarkup(resize_keyboard=True)
    keyboard.add(types.KeyboardButton('subscribe to reply'))

    bot.send_message(user_id, message_text, reply_markup=keyboard)

@bot.message_handler(content_types=['text'])
def echo(message):
    user_id = message.from_user.id
    text = message.text

    if text == "subscribe to reply" and user_id in usersbase:
        bot.send_message(user_id, 'Youre already subscribed.', reply_markup=None)
    
    elif text == 'subscribe to reply':
        usersbase.append(user_id)
        bot.send_message(user_id, "you succesfully subscribed to reply.", reply_markup=None)

    if text.startswith("dsf\n"):
        text = text[4:]
        disassembly_message(text)

def disassembly_message(message):
    for user_id in usersbase:
        bot.send_message(user_id, message)

os.system('cls')
print('bot launch succesful.')

bot.polling(none_stop=True, interval=0)

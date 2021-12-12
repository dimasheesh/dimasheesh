import telebot
from telebot import types

token = '5082363477:AAGmt7omHICAoA1LG2FGxpjpSVuYEnKTk4g'

bot = telebot.TeleBot(token)


@bot.message_handler(commands=['start'])
def start_message(message):
    bot.send_message(message.chat.id, "👋Привет " + message.from_user.first_name + "!" + "\n" +
                     "Это телеграм бот школы Нурмаков и с помощью этого БОТА🤖 Вы можете перейти по ссылке и увидеть наши сайты с работами🖨️, мы разработали панорамы, где можно путешествовать 360 градусов не выходя из дома🗽"
                     "\n" + "Все функции можешь увидеть нажав на- /help")


@bot.message_handler(commands=['help'])
def help(message):
    bot.send_message(message.chat.id, "Эти функции тебе помогут:" + '\n' +
                     '/help - показывает это сообщение⚙' + '\n' +
                     '/map - перенаправляет на нашу карту🗺️' + '\n' +
                     '/insta - показывает инстраграмм страницу школы🏫' + '\n' +
                     '/contacts - показывает как же с нами связаться📱' + '\n' +
                     '/sites - показывает наши сайты')


@bot.message_handler(commands=['map'])
def map(message):
    markup = types.InlineKeyboardMarkup()
    btn_my_site = types.InlineKeyboardButton(text='Карта',
                                             url='https://www.google.com/maps/d/edit?mid=1GUhp2hn2maJl4-iXdBMLLFSeJNyKq8yH&usp=sharing')
    markup.add(btn_my_site)
    bot.send_message(message.chat.id, "Нажми на кнопку и перейди на нашу карту.", reply_markup=markup)


@bot.message_handler(commands=['insta'])
def map(message):
    markup = types.InlineKeyboardMarkup()
    btn_my_site = types.InlineKeyboardButton(text='Instagram',
                                             url='https://instagram.com/nurmakov_school?utm_medium=copy_link')
    markup.add(btn_my_site)
    bot.send_message(message.chat.id, "Нажми на кнопку и перейди на нашу инстаграм стриницу.", reply_markup=markup)


@bot.message_handler(commands=['contacts'])
def contacts(message):
    bot.send_message(message.chat.id, "Место - Школа Нурмакова, Алиханова 36/2a" + '\n'
                                                                                   'email📧 - din.makhmut96@gmail.com')


@bot.message_handler(commands=['sites'])
def sites(message):
    markup = types.InlineKeyboardMarkup()
    btn_my_site = types.InlineKeyboardButton(text='Зоопарк',
                                             url='https://kartakrg.kz/karta-2/karaganda/n-nurmakov-atyndagy-mmi')
    markup1 = types.InlineKeyboardMarkup()
    btn_my_site1 = types.InlineKeyboardButton(text='Городской парк',
                                              url='https://kartakrg.kz/karta/karaganda/sshi-im-n-nurmakova')

    markup.add(btn_my_site, btn_my_site1)
    bot.send_message(message.chat.id, "Нажми на кнопку и перейди на нашу сайту с работами.", reply_markup=markup)


bot.infinity_polling()

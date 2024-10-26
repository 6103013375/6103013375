import requests
import json 
import telebot
import random
from telebot import types

token = "7746679493:AAFdQJn3BgIOCAo6I9faZOORbp8JjBmhk4Q"
bot = telebot.TeleBot(token)

headers = {
    'authority': 'www.fancytextpro.com',
    'accept': 'text/plain, */*; q=0.01',
    'accept-language': 'ar-EG,ar;q=0.9,en-US;q=0.8,en;q=0.7',
    'content-type': 'application/x-www-form-urlencoded; charset=UTF-8',
    'origin': 'https://www.fancytextpro.com',
    'referer': 'https://www.fancytextpro.com/',
    'sec-ch-ua': '"Not:A-Brand";v="99", "Chromium";v="112"',
    'sec-ch-ua-mobile': '?1',
    'sec-ch-ua-platform': '"Android"',
    'sec-fetch-dest': 'empty',
    'sec-fetch-mode': 'cors',
    'sec-fetch-site': 'same-origin',
    'user-agent': 'Mozilla/5.0 (Linux; Android 12; M2004J19C) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/112.0.0.0 Mobile Safari/537.36',
    'x-requested-with': 'XMLHttpRequest',
}

@bot.message_handler(commands=['start'])
def start(message):
	name = message.from_user.first_name
	btn = types.InlineKeyboardButton('إشترك في قناتي رجاءاً',url='t.me/bk_sx5')
	xx = types.InlineKeyboardMarkup()
	xx.add(btn)
	bot.reply_to(message,f'''اهلا بك عزيزي {name}\nارسل اسمك لزغرفته ب30 نوع''',reply_markup=xx)
	
@bot.message_handler(func=lambda m:True)
def text(message):
    data = {
    'text': message.text,
    '_csrf': '',
    'pages[]': [
    'New',
    'Unique',
    'CoolText',],}
    response = requests.post('https://www.fancytextpro.com/generate', headers=headers, data=data)
    data = json.loads(response.content)
    s1 = data['MusicalMap']; s2 = data['neonCharMap'];s3 = data['boldCharMap']; s4 = data['EmojiMap']; s4 = data['italicCharMap'];s5 = data['AncientMap'];s6 = data['Ladyleo'];s7 = data['boldItalicCharMap'];s8 = data['SinoTibetan'];s9 = data['monospaceCharMap'];s10 = data['weirdChar'];s11 = data['BoldFloara'];s12 = data['upperAnglesCharMap'];s13 = data['BuzzChar'];s14 = data['greekCharMap'];s15 = data['SunnyDay'];s16 = data['invertedSquaresCharMap'];s17 = data['TextDecorated'];s18 = data['doubleStruckCharMap'];s19 = data['Dessert'];s20 = data['oldEnglishCharMap'];s21 = data['taiVietCharMap'];s22 = data["oldEnglishCharBoldMap"];s23 = data['oldItalicText'];s24 = data['cursiveLetters'];s25 = data['cursiveLettersBold'];s26 = data['BoldJavaneseText'];s27 = data['wideTextCharMap'];s28 = data['subscriptCharMap'];s29 = data['GunText'];s30 = data['superscriptCharMap'];s31 = data['ak47GunText']
    aa = (s1, s2, s3, s4, s5, s6, s7, s8, s9, s10, s11, s12, s13, s14, s15, s16, s17, s18, s19, s20, s21, s22, s23, s24, s25, s26, s27, s28, s29, s30, s31)
    m = "\n".join(aa)
    bot.reply_to(message, f'<b>{m}\n\nPY : @hFfn3w</b>', parse_mode="HTML")

print('run')
bot.infinity_polling()

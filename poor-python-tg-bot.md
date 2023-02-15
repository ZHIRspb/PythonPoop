---
description: Youtube video downloader + audiofile loader
---

# Poor Python TG Bot

```
import moviepy.editor
from pytube import YouTube
import telebot

yt = ''
stream = ''
video = ''
audio = ''
vid = ''
aud = ''

bot = telebot.TeleBot("6269317752:AAFglq6QXXlCmIseD3RIAB_ObdwDhXTom6A")
@bot.message_handler(commands=['start', 'help'])

def send_welcome(message):
    if message.text == '/start':
       bot.send_message(message.from_user.id, "Привет! Чтобы узнать, что умеет этот бот введи /help")
    elif message.text == '/help':
        bot.send_message(message.from_user.id, "Этот бот умеет скачивать Youtube видео  в формате mp4 720p по отправленной ссылке. Дополнительно к этому он отправит mp3 аудиодорожку данного видео для прослушивания в качестве подкаста. Отправь ссылку чтобы проверить его работу!")

@bot.message_handler(func=lambda m: True)
def send_files(message):
    if 'https://www.youtube.com' in message.text or 'https://youtu.be' in message.text:

        bot.send_message(message.from_user.id, "Подожди немного...")

        global yt
        yt = YouTube(message.text)
        yt.streams.filter(file_extension='mp4')

        global stream
        stream = yt.streams.get_by_itag(22)
        stream.download(filename='video.mp4')

        global video
        video = moviepy.editor.VideoFileClip('video.mp4')

        global audio
        audio = video.audio
        audio.write_audiofile('audio.mp3')

        global vid
        vid = open('C:/Users/tniki/PycharmProjects/video_to_audio/video.mp4', 'rb')
        bot.send_video(message.chat.id, vid)

        global aud
        aud = open('C:/Users/tniki/PycharmProjects/video_to_audio/audio.mp3', 'rb')
        bot.send_audio(message.chat.id, aud)
        
    else:
        bot.send_message(message.from_user.id, "Проверь правильность ссылки (ссылка должна быть формата https://www.yotube.com/video_link или https://youtu.be/video_link)")


bot.infinity_polling()
```

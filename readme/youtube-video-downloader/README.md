---
description: >-
  Download YT video by YT link in 1080p with sound + save audiofile (ssyoutube
  highest res with sound is only 720p)
---

# 📺 Youtube video downloader

```python
import moviepy.editor
from pytube import YouTube
import os

URL = 'https://www.youtube.com/video_link'
yt = YouTube(URL)
tags = yt.streams.filter(file_extension='mp4')

for i in yt.streams.filter(only_audio=True).order_by('abr').all():
    print(i)
audio_tag = int(input('Choose audio download tag: '))

for i in yt.streams.filter(only_video=True).all():
    print(i)
video_tag = int(input('Choose video download tag: '))

fps = int(input('Enter video fps parameter: '))
bitrate = input('Enter bitrate parameter: ')

audio = yt.streams.get_by_itag(audio_tag)
audio.download(filename='audio.mp3')
audio_clip = moviepy.editor.AudioFileClip('audio.mp3')

video = yt.streams.get_by_itag(video_tag)
video.download(filename='vidos.mp4')
video_clip = moviepy.editor.VideoFileClip('vidos.mp4')

final_video = video_clip.set_audio(audio_clip)
final_video.write_videofile('final_video.mp4', fps=fps, codec='h264_nvenc', bitrate)
os.remove('vidos.mp4')

```

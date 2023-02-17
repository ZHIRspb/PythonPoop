---
description: >-
  Download YT video by YT link in 1080p with sound + save audiofile (ssyoutube
  highest res with sound is only 720p)
---

# 📺 Youtube video downloader

```
import moviepy.editor
from pytube import YouTube
import os

URL = 'https://www.youtube.com/video_link'
yt = YouTube(URL)

# print(yt.streams.filter(file_extension='mp4'))

audio = yt.streams.get_by_itag(22)
audio.download(filename='audio.mp4')

video = yt.streams.get_by_itag(399)
video.download(filename='vidos.mp4')
video_clip = moviepy.editor.VideoFileClip('vidos.mp4')

audio_clip = moviepy.editor.AudioFileClip('audio.mp4')
audio_clip.write_audiofile('audio.mp3')

final_video = video_clip.set_audio(audio_clip)
final_video.write_videofile('final_video.mp4', fps=45, threads=16, codec='h264_nvenc', ffmpeg_params=['-b:v', '10000k'], preset='faster')

os.remove('vidos.mp4')
os.remove('audio.mp4')

```

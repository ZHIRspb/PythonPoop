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
audio.download(filename='filename1.mp4') #downloading videofile 720p with sound

video = yt.streams.get_by_itag(399)
video.download(filename='filename2.mp4')
video_clip = moviepy.editor.VideoFileClip('filename2.mp4') #downloading videofile 1080p without sound

audio_clip = moviepy.editor.AudioFileClip('filename.mp4')
audio_clip.write_audiofile('audio.mp3') #making audiofile of 720p video

final_video = video_clip.set_audio(audio_clip) #setting audiofile into 1080p video
final_video.write_videofile('final_video.mp4', fps=45, threads=16, codec='h264_nvenc', ffmpeg_params=['-b:v', '10000k'], preset='faster') #this is my own preset for faster downloading

os.remove('vidos.mp4')
os.remove('audio.mp4')

```

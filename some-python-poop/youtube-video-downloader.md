---
description: Download yt video by yt link
---

# 📺 Youtube video downloader

```
from pytube import YouTube

yt = YouTube('https://www.youtube.com/video_link')

print(yt.streams.filter(file_extension='mp4'))
stream = yt.streams.get_by_itag(22)
stream.download()
```

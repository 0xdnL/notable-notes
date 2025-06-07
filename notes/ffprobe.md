---
tags: [linux]
title: ffprobe
created: '2024-07-08T07:40:05.926Z'
modified: '2025-03-20T09:35:35.753Z'
---

# ffprobe

> ffprobe media prober

[[ffmpeg]], [[ffplay]]

## install

```sh
brew install ffmpeg
```

## usage

```sh
ffprobe -v error -select_streams v:0 -show_entries stream=width,height cover.jpg      # get dimensions

ffprobe -v error -select_streams v:0 -show_entries stream=codec_name -of default=nokey=1:noprint_wrappers=1 file.mp4 # get encoding
```

## see also

- [[file]]
- [[imagemagick]]
- [[youtube-dl]]

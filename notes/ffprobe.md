---
tags: [linux]
title: ffprobe
created: '2024-07-08T07:40:05.926Z'
modified: '2024-10-08T09:23:35.078Z'
---

# ffprobe

> ffprobe media prober

## install

```sh
brew install ffmpeg
```

## usage

```sh
ffprobe -v error -select_streams v:0 -show_entries stream=width,height cover.jpg      # get dimensions
```

## see also

- [[ffmpeg]]
- [[ffplay]]
- [[imagemagick]]
- [[youtube-dl]]

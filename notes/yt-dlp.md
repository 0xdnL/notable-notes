---
tags: [python]
title: yt-dlp
created: '2025-06-07T08:51:50.009Z'
modified: '2025-06-07T08:58:48.001Z'
---

# yt-dlp

> a feature-rich cli audio/video downloader,  fork of [[youtube-dl]] based on the now inactive [[youtube-dlc]]

[github.com/yt-dlp/yt-dlp](https://github.com/yt-dlp/yt-dlp)

## install

```sh
python3 -m venv ./venv
source ./venv/bin/activate

pip install yt-dlp --upgrade
```

[[python]], [[pip]], [[virtualenv]]

## usage

```sh
yt-dlp --extract-audio --audio-format mp3 -o "%(artist)s-%(title)s-%(id)s.%(ext)s" -v -- URL

yt-dlp --extract-audio --audio-format mp3 --split-chapters -o "chapter:R:\YouTube\%(title)s\%(section_number)03d. %(section_title)s.%(ext)s" -v -- URL
```

## see also

- [[curl]]
- [[ffmpeg]]

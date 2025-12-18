---
tags: [python]
title: youtube-dl
created: '2019-07-30T06:19:49.267Z'
modified: '2025-11-24T10:22:05.307Z'
---

# youtube-dl

> download videos from youtube.com or other video platforms

[[yt-dlp]]

## install

```sh
pip install --upgrade youtube-dl  # vent and pip install

curl -LO https://yt-dl.org/downloads/latest/youtube-dl # move to path and chmod a+rx FILE
```

[[pip]] [[venv]]

## usage

```sh
youtube-dl --continue --extract-audio --audio-format mp3 --embed-thumbnail h3Q12OkBTHk

youtube-dl --continue --extract-audio --audio-format mp3 --embed-thumbnail --batch-file FILE

youtube-dl --skip-download --write-thumbnail VIDEO_ID    # download just the thumbnail from a youtube video

youtube-dl \
  --extract-audio \
  -f bestaudio \
  -o '/PATH/FILE.mp3' \
  --metadata-from-title "%(artist)s - %(title)s" \
  YOUTUBE_ID 2>&1

youtube-dl `# extract audio from playlist starting at playlist-index: 17` \
  --no-overwrites \
  --continue \
  --extract-audio \
  --audio-format mp3 \
  --playlist-start 17 \
  LIST_ID

youtube-dl -j --flat-playlist LIST_ID | jq  -r --arg START 00 '($START | tonumber) as $s | "\($s) - \(.title)-\(.id)"'
```

## output template

```sh

youtube-dl -o "%(playlist_index)02d - %(title)s.%(ext)s"            LIST_ID
youtube-dl -o "%(playlist)s\%(playlist_index)s - %(title)s.%(ext)s" LIST_ID
youtube-dl -o "%(playlist_index)s-%(title)s.%(ext)s"                LIST_ID
youtube-dl -o "%(autonumber)s-%(title)s.%(ext)s"                    LIST_ID

# checkout: -j, --dump-json 
```

[github.com/ytdl-org/youtube-dl/README.md#output-template](https://github.com/ytdl-org/youtube-dl/blob/master/README.md#output-template)

## see also

- [[jq]]
- [[imagemagick]]
- [[ffmpeg]]
- [[eyed3]]


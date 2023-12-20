---
tags: [python]
title: youtube-dl
created: '2019-07-30T06:19:49.267Z'
modified: '2023-11-20T18:38:56.885Z'
---

# youtube-dl

> download videos from youtube.com or other video platforms

## install

```sh
brew install youtube-dl

pip install --upgrade youtube-dl

curl -LO https://yt-dl.org/downloads/latest/youtube-dl # move to path and chmod a+rx FILE
```

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
```

## see also

- [[imagemagick]]
- [[ffmpeg]]
- [[eyed3]]
- [[pip]]
- [[curl]]
- [[chmod]]

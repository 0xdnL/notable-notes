---
tags: [linux, macos]
title: ffmpeg
created: '2021-03-10T11:11:18.975Z'
modified: '2025-03-20T09:35:59.593Z'
---

# ffmpeg

> video and audio converter 

[[ffprobe]], [[ffplay]]

## install

```sh
brew install ffmpeg
```

## usage

```sh
ffmpeg -i FILE.mp3 -ss 00:00:00 -to 00:00:20 -c copy COPY.mp3   # crop audio file's first 20sek
```

## filter:crop

> `crop=out_w:out_h:x:y`

```sh
# crop center 720x720 of image
# The output width and height (`out_w` and `out_h`) are both 720.
# To center the crop, you calculate `x` and `y` as follows:
#  - `x` = (`original_width` - `out_w`) / 2 = (1280 - 720) / 2 = 280
#  - `y` = (`original_height` - `out_h`) / 2 = (720 - 720) / 2 = 0
ffmpeg -i cover.jpg -vf "crop=720:720:280:0" output.jpg
```

## convert formats

```sh
ffmpeg -i FILE.webm -vn -q:a 0 -map a out.mp3                                               # convert .webm to .mp3
ffmpeg -i FILE.webp FILE.png                                                                # convert .webp to .png

ffmpeg -i FILE.mov -vcodec h264 -acodec mp2 FILE.mp4                                        # convert .mov to .mp4
ffmpeg -i FILE.mov -c:v libvpx -crf 10 -b:v 1M -c:a libvorbis FILE.webm                     # convert .mov to .webm
ffmpeg -i FILE.mov -codec:v libtheora -qscale:v 7 -codec:a libvorbis -qscale:a 5 FILE.ogg   # convert .mov to .ogg

ffmpeg -i FILE.mov \                                                                       `# convert .mov to .gif`
  -filter_complex "[0:v] fps=12,scale=2048:-1,split [a][b];[a] palettegen [p];[b][p] paletteuse" FILE.gif

ffmpeg -ss 00:01:30 -i downloaded_video.mp4 -frames:v 1 thumbnail.jpg       # extract a thumbnail from video frame
```

## see also

- [[imagemagick]]
- [[youtube-dl]]

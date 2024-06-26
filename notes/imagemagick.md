---
tags: [linux, macos]
title: imagemagick
created: '2020-12-28T21:19:42.860Z'
modified: '2023-12-22T14:02:47.420Z'
---

# imagemagick

> create, edit, compose, or convert bitmap images, can read and write images in a variety of formats

## install

```sh
brew install imagemagick
```

## convert

```sh
convert IMAGE.png -resize 128x128 IMAGE_resized.png       # resize image
convert IMAGE.gif -resize 50%  half_IMAGE.gif

# generate pdf file
convert xc:none -page Letter  FILE.pdf
convert xc:none -page A4      FILE.pdf
convert xc:none -page 842x595 FILE.pdf

convert FILE.txt -page Letter FILE.pdf

convert "*.{png,jpeg}" -quality 100 outfile.pdf

convert -density 600 FILE1.pdf FILE2.pdf -resize 50% NEW_FILE.pdf

# make an impact image
convert \
  -size 1000x600 \
  -define gradient:radii=1000,500 radial-gradient:#884b88-#010101 \
  -font Impact \
  -pointsize 72 \
  -fill white \
  -gravity center \
  -interline-spacing 50 \
  -annotate 0,0 "Now with more arguments!" now-with-more-arguments.png
```

## see also

- [imagemagick.org/script/convert](https://imagemagick.org/script/convert.php)
- [legacy.imagemagick.org/Usage/resize](https://legacy.imagemagick.org/Usage/resize/)
- [[ffmpeg]]
- [[gs]]
- [[youtube-dl]]
- [[exiftool]]

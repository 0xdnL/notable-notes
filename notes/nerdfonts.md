---
tags: [linux, macos]
title: nerdfonts
created: '2023-04-15T09:17:30.144Z'
modified: '2025-10-09T08:07:10.486Z'
---

# nerdfonts

> patches developer targeted fonts with a high number of glyphs (icons)
> Specifically to adds a high number of extra glyphs from popular ‘iconic fonts’ such as `Font Awesome`, `Devicons`, `Octicons`

[nerdfonts.com](https://www.nerdfonts.com/)

- `mono` - monospaced font, also called a fixed-pitch, fixed-width, or non-proportional font, is a font whose letters and characters each occupy the same amount of horizontal space

## install

```sh
brew search '/font-.*-nerd-font/'                   # list available nerdfonts

brew install --cask font-ubuntu-mono-nerd-font      # install font
```

## usage

```sh
# possible path for installed fonts
/System/Library/Fonts/
/Library/Fonts/
~/Library/Fonts/


fc-list | grep -v "/System" | column -t -s:
/PATH/TO/Library/Fonts/Ubuntu Mono Bold Italic Nerd Font Complete Mono.ttf: UbuntuMono Nerd Font Mono:style=Bold Italic
#                                                                          └─────────────────────────┘

fc-list                                 # lists all font faces
fc-list :lang=hi                        # lists font faces that cover Hindi. 
fc-list : family style file spacing     # lists filename and spacing value for each font face. '':'' is an empty pattern that matches all fonts
fc-list : file family | grep \/Library

fc-cache    # scan font files or directories
```


## see also

- [[brew]]
- [[alacritty]], [[ghostty]]
- [[vim]], [[nvim]], [[nvchad]]

---
tags: [linux, macos]
title: tree
created: '2019-10-05T03:18:36.580Z'
modified: '2025-12-28T09:12:26.716Z'
---

# tree

> list contents of directories in a tree-like format

## install

```sh
brew install tree
```

## environment

```sh
LS_COLORS             # Color information created by dircolors
TREE_COLORS           # Uses this for color information over LS_COLORS if it is set
TREE_CHARSET          # Character set for tree to use in HTML mode.
CLICOLOR              # enables colorization even if TREE_COLORS or LS_COLORS is not set
CLICOLOR_FORCE        # always enables colorization
NO_COLOR              # disable colorization
LC_CTYPE              # locale for filename output
LC_TIME               # locale for timefmt output, see strftime(3)
TZ                    # timezone for timefmt output, see strftime(3)
STDDATA_FD            # Enable the stddata feature, optionally set descriptor to use
```

[no-color.org](https://no-color.org/)

## options

```sh
-d            # list directories only
-l            # follows symbolic links
-L level      # max display depth of the directory tree

-n            # turn colorization off always
```

## usage

```sh
tree -d -L 3 .      # show only directory to level 3
```

## see also

- [[ls]]
- [[find]]

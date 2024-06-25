---
tags: [linux, macos]
title: uniname
created: '2023-12-06T12:03:59.708Z'
modified: '2024-02-08T09:33:43.286Z'
---

# uniname

> name characters in [[unicode]] file, for each character, prints the character and byte offsets, etc.

## install

```sh
brew install uniutils
```

## option

```sh
-a        # Skip ASCII characters
-A        # Skip ASCII whitespace characters
-B        # Skip characters within the BMP
-s        # <character offset>  skip to specified character
-S        # <byte offset>  skip to specified byte
-l        # Supply line number
-r        # Supply Unicode range
-b        # Suppress printing of byte offset
-c        # Suppress printing of character offset
-e        # Suppress printing of encoding
-g        # Suppress printing of glyph
-p        # Suppress printing of headers every screenfull
-n        # Suppress printing of Unicode name
-u        # Suppress printing of UTF-32 code
-h        # Print help information
-v        # Print version information
-q        # Input is native-order UTF-32 [default is UTF-8]
-V        # Validate input (determine whether it is valid UTF-8)
```

## usage

```sh
uniname <<< '🍕'
```

## see also

- [[unicode]]
- [[ascii]]

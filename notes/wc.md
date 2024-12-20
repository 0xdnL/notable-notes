---
tags: [linux]
title: wc
created: '2022-11-29T08:07:33.392Z'
modified: '2024-12-04T10:19:36.064Z'
---

# wc

> word, line, character, and byte count contained in each input

## option

```sh
-c      # number of bytes      in each input file is written to the STDOUT
-l      # number of lines      in each input file is written to the STDOUT
-m      # number of characters in each input file is written to the STDOUT
-w      # number of words      in each input file is written to the STDOUT
```

## usage

```sh
CMD | wc -l | xargs     # pipe to xargs to trim spaces

echo STRING | wc -c

history | wc
8744   61819  628428
# no lines, words, bytes
```

```sh
wc -l < FILE 
61

wc -l FILE 
61 FILE
```

[[bash redirects]]

## see also

- [[grep]]
- [[xargs]]
- [[bash history]]

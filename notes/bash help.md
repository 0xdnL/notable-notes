---
tags: [shell/bash/builtin]
title: bash help
created: '2019-08-02T06:42:37.601Z'
modified: '2024-11-14T13:43:34.403Z'
---

# bash help

> display information about builtin commands

## option

```sh
-d              # output short description
-m              # display usage in pseudo-manpage format
-s              # output only a short usage synopsis for each topic matching PATTERN
```

## usage

```sh
help            # displays brief summaries of builtin commands

help CMD        # find out more about the function CMD

man -k          # find out more about commands not in this list
info            # find out more about commands not in this list
info bash       # find out more about the shell in general
```

## see also

- [[man]]
- [[command-not-found]]
- [[bash \[\[]]
- [[zsh run-help]]

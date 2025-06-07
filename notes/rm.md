---
tags: [coreutils, linux, macos]
title: rm
created: '2019-08-22T07:14:59.460Z'
modified: '2024-12-20T11:01:48.769Z'
---

# rm

> remove directory entries

alternative to [[rip]]

## usage

```sh
rm -f  FILE     # ignore nonexistent files and arguments, never prompt

rm -r DIR       # remove all files contained within DIR recursively

rm -- -f        # remove file named `-f`

rm ./-f         # remove file named `-f`

rm \~           # no bash expantion from `~` to $HOMEDIR
```

## see also

- [[unlink]]
- [[bash]]
- [[mv]]
- [[cp]]

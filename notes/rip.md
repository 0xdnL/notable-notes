---
tags: [linux, macos, rust]
title: rip
created: '2021-05-27T09:10:45.980Z'
modified: '2024-12-20T11:01:41.563Z'
---

# rip

> `rm ImProved` - cli deletion tool focused on safety, ergonomics, and performance
> does not implement the `xdg-trash`
> deleted files get sent to the graveyard (`/tmp/graveyard-$USER` by default

alternative to [[rm]]

## install

```sh
cargo install rm-improved

brew install rm-improved
```

[[cargo]]

## option

```sh
-d, --decompose    permanently deletes (unlink) the entire graveyard
```

## usage

```sh
rip -u      # undo last deletion
```

## see also

- [github.com/nivekuil/rip](https://github.com/nivekuil/rip)
- [[unlink]]

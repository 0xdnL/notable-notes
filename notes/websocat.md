---
tags: [linux]
title: websocat
created: '2024-09-25T09:54:54.708Z'
modified: '2024-10-08T09:23:35.049Z'
---

# websocat

> [[nc]], [[curl]] and [[socat]] for websockets

## install

```sh
brew install websocat
```

## usage

```sh
websocat ws://HOST/ws

websocat -q -uU ws://HOST/ws    # check if connection works


websocat -s 1234
Listening on ws://127.0.0.1:1234/
ABC
123

websocat ws://127.0.0.1:1234/
ABC
123
```

## see also

- [[socat]]
- [[nghttp]]
- [github.com/vi/websocat](https://github.com/vi/websocat)

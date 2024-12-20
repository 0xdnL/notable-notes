---
tags: [lua, packagemanager]
title: luarocks
created: '2020-09-02T13:03:43.096Z'
modified: '2024-11-22T11:42:20.715Z'
---

# luarocks

> package manager for [[lua]] modules

## install

```sh
wget https://luarocks.org/releases/luarocks-${VERSION}.tar.gz
tar zxpf luarocks-${VERSION}.tar.gz
cd luarocks-${VERSION}
```

## usage

```sh
luarocks                      #  see the available commands

luarocks help install         # get help on command

luarocks install dkjson       # installing packages

luarocks make
```

## see also

- [[nvim]]
- [[luac]]
- [[make]]

---
tags: [shell/bash/builtin]
title: bash alias
created: '2019-08-02T06:42:37.554Z'
modified: '2023-11-18T13:02:46.284Z'
---

# bash alias

> define or display aliases

## option

```sh
-p        # print all defined aliases in a reusable format
```

## usage

```sh
alias             # prints all aliases

alias l='ls -l'   # define alias
```

## use alias to intercept to change future invocation

```sh
ls
alias ls='/usr/bin/time ls'
ls
unalias ls
```

## see also

- [[bash complete]]
- [[bash unalias]]
- [[git log]]
- [[time]]
- [cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix/](https://www.cyberciti.biz/tips/bash-aliases-mac-centos-linux-unix.html/)

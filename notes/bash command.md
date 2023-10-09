---
tags: [shell/bash/builtin]
title: bash command
created: '2019-08-02T06:42:37.566Z'
modified: '2023-09-14T06:47:26.878Z'
---

# bash command

> execute a simple command or display information about commands 
suppressing  shell function lookup, or display information about the specified COMMANDs

## option

```sh
-p        # use a default value for PATH that is guaranteed to find all of the standard utilities
-v        # print a description of COMMAND similar to the `type' builtin
-V        # print a more verbose description of each COMMAND
```

## usage

```sh
command -v CMD    # posix way of checking if CMD is available
```

## see also

- [[which]]
- [[bash type]]
- [[bash hash]]

---
tags: [shell/bash/builtin]
title: bash command
created: '2019-08-02T06:42:37.566Z'
modified: '2025-12-05T12:20:02.074Z'
---

# bash command

> execute a simple command or display information about commands 
suppressing  shell function lookup, or display information about the specified COMMANDs

[[sleep]]

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

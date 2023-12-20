---
tags: [shell/bash]
title: bash unset
created: '2022-02-10T09:01:46.925Z'
modified: '2023-11-20T18:26:40.682Z'
---

# bash unset

> unset values and attributes of shell variables and functions

## option

```sh
-f        # treat each NAME as a shell function
-v        # treat each NAME as a shell variable
-n        # treat each NAME as a name reference and unset the variable itself rather than the variable it references
```

## usage

```sh
unset           # Without options, unset first tries to unset a variable, and if that fails,tries to unset a function
                # Some variables cannot be unset; also see `readonly'

unset -v ${!DOCKER_*}   # unset all variables starting with DOCKER_
```

## see also

- [[env]]
- [[bash set]]
- [[bash readonly]]
- [[bash function]]

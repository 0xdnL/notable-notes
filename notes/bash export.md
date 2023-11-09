---
tags: [shell/bash/builtin]
title: bash export
created: '2019-08-02T06:42:37.589Z'
modified: '2023-10-14T10:29:02.360Z'
---

# bash export

> export will make variables/functions available to all shells forked from the current shell.

## option

```sh
-f                    # refer to shell functions
-n                    # remove the export property from each NAME
-p                    # display a list of all exported variables and functions
--                    # disables further option processing.
```

## usage

```sh
export -p               # list exported variables and functions, same as `declare -x`

export -n               # remove the export property from each NAME

export -f myFunc        # pass function to any child processes

export A=1 B=2 C=3      # mutliple vairables

 export TOKEN=secret    # space before export ensure not saving to history
```

## see also

- [[env]]
- [[bash]]
- [[bash history]]
- [[bash declare]]
- [[bash set]]
- [[bash unset]]
- [[bash declare]]
- [[heredoc]]

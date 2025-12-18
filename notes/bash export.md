---
tags: [shell/bash/builtin]
title: bash export
created: '2019-08-02T06:42:37.589Z'
modified: '2025-10-26T13:25:01.365Z'
---

# bash export

> export will make variables/functions available to all shells forked from the current shell

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

export TOKEN=secret     # space before export ensure not saving to history
```

can also be exported using [[bash declare]] which is more bash specific

## see also

- [[env]]
- [[bash]]
- [[bash history]]
- [[bash set]]
- [[bash unset]]
- [[bash declare]]
- [[heredoc]]

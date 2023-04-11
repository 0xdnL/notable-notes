---
tags: [shell/bash/builtin]
title: bash echo
created: '2019-08-02T06:42:37.582Z'
modified: '2022-11-25T11:23:48.428Z'
---

# bash echo

> write arguments to stdout

## option

```sh
-n        # do not append a newline
-e        # enable interpretation of the following backslash escapes
-E        # explicitly suppress interpretation of backslash escapes
```

## usage

```sh
echo -n "USER:PWD" | base64     # not linebreak !
```

## see also

- [[bash printf]]
- [[base64]]
- [[bash variables]]
- [[od]]

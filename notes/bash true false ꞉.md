---
tags: [shell/bash/builtin]
title: 'bash true false :'
created: '2019-08-02T06:42:37.640Z'
modified: '2025-12-05T12:24:00.541Z'
---

# bash true false :

> return a successful result

[[bash]]

## usage

```sh
: ${A:=hello}     # assign a default value

while :; do echo 'hit ctrl+c to exit'; sleep 1; done    # infinite loop
```

## not true but a fork bomb

> function named `:`

```sh
:(){ :|:& };:


bomb() { 
 bomb | bomb &
}; bomb
```

## see also

- [[bash while]]
- [[bash parameter expansion]]

---
tags: [shell/bash/builtin]
title: bash shift
created: '2019-08-02T06:42:37.629Z'
modified: '2021-05-12T08:46:08.424Z'
---

# bash shift

> shift positional parameters

## usage
```sh
for i in "$@"; do
  case $i in
    -e=*|--environment=*)
    echo "case i: ${i#*=}"
    CMD+=('-e '${i#*=})
    shift;
  esac
done
```

## see also
- [[bash arguments]]

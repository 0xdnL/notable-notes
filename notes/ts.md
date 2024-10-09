---
tags: [linux]
title: ts
created: '2024-07-30T06:31:07.691Z'
modified: '2024-10-08T09:20:37.187Z'
---

# ts

> adds a timestamp to the beginning of each line of input

## usage

```sh
# add timestamp
pg_amcheck -U postgres --install-missing --jobs=8 --verbose --progress --heapallindexed --parent-check 2>&1 \
  | ts \
  | tee -a pg_amcheck.$(date "+%F-%H-%M").log
```

## see also

- [[date]]
- [[moreutils]]

---
tags: [shell/bash/keyword]
title: bash while
created: '2019-07-30T06:19:49.024Z'
modified: '2025-12-05T12:21:18.252Z'
---

# bash while

> execute commands as long they succeed

## usage

```sh
while condition; do statements done


find . | while read; do echo $REPLY; done


while read; do eval echo "$REPLY"; done < config.yml
```

## safe_sleep.sh example using SECONDS

```sh
SECONDS=0   # counts real elapsed time, not exactly ticking each second inside the loop (especially if script is preempted, or the CPU is busy)

# while [[ $SECONDS != $1 ]]; do    # could potentially reach: [[ 6 != 5 ]]
while [[ $SECONDS -lt $1 ]]; do
    :
done
```

[[bash]] `SECONDS`, [[sleep]], [github.com/actions/runner/pull/3157/files](https://github.com/actions/runner/pull/3157/files)

## see also

- [[watch]]
- [[bash for]]
- [[bash read]]
- [[bash until]]
- [[bash true false ꞉]]

---
tags: [shell/bash/keyword]
title: bash while
created: '2019-07-30T06:19:49.024Z'
modified: '2023-11-29T09:24:20.053Z'
---

# bash while

> execute commands as long they succeed

## usage

```sh
while condition; do statements done


find . | while read; do echo $REPLY; done


while read; do eval echo "$REPLY"; done < config.yml
```

## see also

- [[watch]]
- [[bash for]]
- [[bash read]]
- [[bash until]]

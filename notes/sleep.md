---
tags: [linux, shell/bash]
title: sleep
created: '2020-03-26T10:22:21.098Z'
modified: '2025-12-05T12:20:48.242Z'
---

# sleep

> suspend execution for an interval of time

[[coreutils]]

## usage

```sh
sleep 1
```

##  safe_sleep()

> github implementation in case sleep is not present

```sh
safe_sleep() {
  if [ ! -x "$(command -v sleep)" ]; then
    if [ ! -x "$(command -v ping)" ]; then
      COUNT="0"
      while [[ $COUNT != 5000 ]]; do
        echo "SLEEP" > /dev/null
        COUNT=$[$COUNT+1]
      done
    else
      ping -c 5 127.0.0.1 > /dev/null
    fi
  else
    sleep 5
  fi
}
```

[[bash while]], [[bash command]], [[ping]], [github.com/actions/runner/pull/1707/files](https://github.com/actions/runner/pull/1707/files)

## see also

- [[bash while]] safe_sleep
- [[timeout]]
- [[bash until]]

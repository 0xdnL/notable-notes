---
tags: [filesystem]
title: tmpfs
created: '2020-02-20T09:44:43.272Z'
modified: '2025-11-12T18:50:11.824Z'
---

# tmpfs

> temporary filesystem that resides in memory and/or swap partition - way of speeding up accesses to files or automatically clearing on reboot

[[filesystem hierarchy standard]]

## usage

```sh
findmnt /tmp

cd "$(mktemp -d)"     # change to random temp-dir for testing
```

## see also

- [[df]]
- [[mount]]
- [[findmnt]]
- [[mktemp]]

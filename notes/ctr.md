---
tags: [container]
title: ctr
created: '2020-03-12T13:48:00.174Z'
modified: '2022-01-27T09:45:28.586Z'
---

# ctr

> default cli named ctr based on the GRPC api - create and manage containers run with containerd

## usage

```sh
ctr --help                # very helpful

ctr tasks ls              # list current running services

ctr containers start redis /containers/redis

ctr events                # get events
```

## see also

- [github.com/projectatomic/containerd/cli](https://github.com/projectatomic/containerd/blob/master/docs/cli.md)
- [[containerd]]
- [[linuxkit]]
- [[docker]]
- [[crictl]]

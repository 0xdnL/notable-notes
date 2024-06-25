---
tags: [linux, network]
title: brctl
created: '2019-08-28T12:22:49.494Z'
modified: '2024-01-11T12:44:53.836Z'
---

# brctl

> `brctl` ethernet bridge administration is used to set up, maintain, and inspect the ethernet bridge configuration in the linux kernel

## install 

```sh
yum install bridge-utils
```

## usage

```sh
ip add show docker0

brctl show docker0
```

## see also

- [[docker]]
- [[ip]]


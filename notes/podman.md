---
tags: [container]
title: podman
created: '2021-09-06T12:17:24.319Z'
modified: '2023-05-30T07:23:55.859Z'
---

# podman

> manage pods, containers and images

## install

```sh
brew install podman
```

## usage

```sh
podman machine init

podman machine start

podman machine list

podman machine ssh

podman build -t TAG .

podman run -ti --rm IMAGE
```

## see also

- [[docker]]
- [[colima]]
- [[skopeo]]
- [[crc]]

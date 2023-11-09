---
tags: [container]
title: crictl
created: '2021-05-27T09:57:46.096Z'
modified: '2023-10-14T10:48:39.451Z'
---

# crictl

> `cri-o`  - cli for CRI-compatible container runtimes

## install

```sh
dnf install cri-tools
```

## usage

```sh
crictl start CONTAINER_ID

crictl inspect CONTAINER_ID

crictl ps -a

crictl pods
crictl pods --label run=nginx

crictl images nginx
```

## see also

- [[docker]], [[podman]]
- [[ctr]]
- [[kubectl]], [[k3s]]
- [[skopeo]]
- [[buildah]]
- [cri-o.io](https://cri-o.io/)
- [github.com/cri-o/tutorials/crictl](https://github.com/cri-o/cri-o/blob/master/tutorials/crictl.md)

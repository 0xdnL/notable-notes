---
tags: [container]
title: containerd
created: '2020-03-12T13:44:44.636Z'
modified: '2023-11-08T14:38:33.532Z'
---

# containerd

> container runtime with an emphasis on simplicity, robustness and portability

## install

```sh
wget https://github.com/containerd/containerd/archive/v1.3.2.zip && unzip v1.3.2.zip
```

## usage

```sh
containerd config default > /etc/containerd/config.toml   # genrate default config
```

GPRC General Remote Procedure Call
CNCF Cloud Native Computing Foundation
"rich-client"-model

```
+---------------------------------------------------------+
|                  docker architecture                    |
+----------------+--------------+-----------------+-------+
|    docker      | containerd   | containerd-shim | runc  |
| engine/daemon  |              |                 |       |
+----------------+--------------+-----------------+-------+

           cli
            v
   docker engine/daemon
            v
       containerd
            |
    +-------+--------+
    v       v        v
   shim    shim    shim
   runc    runc    runc
```

## see also

- [[zip]]
- [[ctr]]
- [[docker]]
- [[podman]]
- [[nerdctl]]
- [[container]]
- [containerd.io/docs/getting-started](https://containerd.io/docs/getting-started/)

---
tags: [container]
title: containerd
created: '2020-03-12T13:44:44.636Z'
modified: '2025-04-27T12:25:43.051Z'
---

# containerd

> container runtime with an emphasis on simplicity, robustness and portability

needs [[runc]] to start containers
contains[[ctr]] for basic management

[[crictl]] [[docker]]

## install

```sh
curl -LO https://github.com/containerd/containerd/releases/download/v2.0.5/containerd-2.0.5-linux-amd64.tar.gz
curl -LO https://github.com/containerd/containerd/releases/download/v2.0.5/containerd-2.0.5-linux-amd64.tar.gz.sha256sum
sha256sum -c containerd-2.0.5-linux-ajmd64.tar.gz.sha256sum containerd-2.0.5-linux-amd64.tar.gz
tar Cxzvf /usr/local/ containerd-2.0.5-linux-amd64.tar.gz

curl -LO https://raw.githubusercontent.com/containerd/containerd/main/containerd.service
mkdir -p /usr/local/lib/systemd/system/
mv containerd.service /usr/local/lib/systemd/system/containerd.service
systemctl daemon-reload
systemctl enable --now containerd
systemctl status containerd.service
```

[github.com/containerd/containerd/docs/getting-started.md](https://github.com/containerd/containerd/blob/main/docs/getting-started.md) | [[sha256sum]] | [[tar]] | [[systemctl]]

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
- [[sysctl]]

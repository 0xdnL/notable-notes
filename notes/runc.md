---
tags: [container]
title: runc
created: '2020-03-12T13:59:22.450Z'
modified: '2025-04-27T12:21:28.038Z'
---

# runc

> cli for spawning and running containers according to OCI specification

`runc` is a component of [[containerd]] and handles kernel level interactions for running containers

```sh
╭────────╮        ╭──────────────────╮  ╭──────────╮  ╭──────╮  ╭───────────╮
│ docker ├────────┤ containerd/cri-o ├──┤ OCI spec ├──┤ runc ├──┤ container │
╰────────╯        ╰──────────────────╯  ╰──────────╯  ╰──────╯  ╰───────────╯
╭─────╮  ╭─────╮  ╭──────────────────╮  ╭──────────╮  ╭──────╮  ╭───────────╮
│ k8s ├──┤ CRI ├──┤ containerd/cri-o ├──┤ OCI spec ├──┤ runc ├──┤ container │
╰─────╯  ╰─────╯  ╰──────────────────╯  ╰──────────╯  ╰──────╯  ╰───────────╯
```

## install

```sh
curl -LO https://github.com/opencontainers/runc/releases/download/v1.1.12/runc.amd64
curl -LO https://github.com/opencontainers/runc/releases/download/v1.1.12/runc.sha256sum
cat runc.sha256sum | grep runc.amd64 | sha256sum --check

install -m 755 runc.amd64 /usr/local/sbin/runc
```

[[install]]

## usage

```sh
runc create mycontainerid       # run as root

runc list                       # view the container is created and in the "created" state

runc start mycontainerid        # start the process inside the container

runc list                       # after 5 seconds view that the container has exited and is now in the stopped state

runc delete mycontainerid       # now delete the container
```

## see also

- [[docker]]
- [[ctr]], [[nerdctl]]
- [[kubectl]]
- [github.com/opencontainers/runc](https://github.com/opencontainers/runc)

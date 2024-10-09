---
tags: [container]
title: crictl
created: '2021-05-27T09:57:46.096Z'
modified: '2024-09-30T08:09:35.462Z'
---

# crictl

> `cri-o`, interact with container runtimes that implement the kubernetes cri

## install

```sh
dnf install cri-tools
```

## attach

> Attach to a running container

```sh
crictl attach
```

[iximiuz.com/en/posts/containers-101-attach-vs-exec](https://iximiuz.com/en/posts/containers-101-attach-vs-exec/)

## create

> Create a new container

```sh
crictl create
```

## exec

> Run a command in a running container

```sh
crictl exec
```

## version

> Display runtime version information

```sh
crictl version
```

## images

> List images

```sh
crictl images nginx
```

## inspect

> Display the status of one or more containers

```sh
crictl inspect
```

## inspecti

> Return the status of one or more images

```sh
crictl inspecti
```

## imagefsinfo

> Return image filesystem info

```sh
crictl imagefsinfo
```

## inspectp

> Display the status of one or more pods

```sh
crictl inspectp
```

## logs

> Fetch the logs of a container

```sh
crictl logs
```

## port

> forward        Forward local port to a pod

```sh
crictl port-forward
```

## ps

> List containers

```sh
crictl ps -a
```

## pull

> Pull an image from a registry

```sh
crictl pull
```

## run

> Run a new container inside a sandbox

```sh
crictl run
```

## runp

> Run a new pod

```sh
crictl runp
```

## rm

> Remove one or more containers

```sh
crictl rm
```

## rmi

> Remove one or more images

```sh
crictl rmi
```

## rmp

> Remove one or more pods

```sh
crictl rmp
```

## pods

> List pods

```sh
crictl pods
crictl pods --label run=nginx
```

## start

> Start one or more created containers

```sh
crictl start
```

## info

> Display information of the container runtime

```sh
crictl info
```

## stop

> Stop one or more running `containers`

```sh
crictl stop
```

## stopp

> Stop one or more running `pods`

```sh
crictl stopp
```

## update

> Update one or more running containers

```sh
crictl update
```

## config

> Get and set crictl client configuration options

```sh
crictl config
```

## stats

> List container(s) resource usage statistics

```sh
crictl stats
```

## statsp

> List pod resource usage statistics

```sh
crictl statsp
```

## completion

> Output shell completion code

```sh
crictl completion
```

## help

>  Shows a list of commands or help for one command

```sh
crictl help
```

## see also

- [[docker]], [[podman]], [[ctr]], [[kubectl]]
- [[skopeo]], [[buildah]]
- [cri-o.io](https://cri-o.io/)
- [github.com/cri-o/tutorials/crictl](https://github.com/cri-o/cri-o/blob/master/tutorials/crictl.md)
- [kubernetes.io/docs/tasks/debug/debug-cluster/crictl/](https://kubernetes.io/docs/tasks/debug/debug-cluster/crictl/)


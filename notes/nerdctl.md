---
tags: [container]
title: nerdctl
created: '2022-01-27T09:39:31.754Z'
modified: '2024-11-16T05:13:53.622Z'
---

# nerdctl

> [[docker]] compatible cli for [[containerd]]

## install

```sh
brew install nerdctl
```

bundled with [[rdctl]]

## usage

```sh
nerdctl run -it --rm alpine                           # run a container with the default bridge CNI network (10.4.0.0/24)

nerdctl build -t foo /some-dockerfile-directory       #  build an image using BuildKit

nerdctl build -o type=local,dest=. /DIR               # build and send output to a local directory using BuildKit

nerdctl compose -f ./docker-compose.yaml up           # run containers from docker-compose.yaml

nerdctl --namespace k8s.io ps -a                      # list Kubernetes containers

nerdctl run -d -p 8080:80 --name nginx nginx:alpine   # run a container with rootless containerd
```

## see also

- [[ctr]]
- [[kim]]
- [[colima]]
- [[docker]]
- [[docker-compose]]
- [[containerd]]
- [[kubectl]]

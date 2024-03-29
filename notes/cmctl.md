---
tags: [container]
title: cmctl
created: '2022-03-16T06:30:28.296Z'
modified: '2023-10-14T12:02:45.571Z'
---

# cmctl

> cli for managing `cert-manager` resources inside kubernetes

## install

```sh
OS=$(go env GOOS); ARCH=$(go env GOARCH); curl -sSLO https://github.com/cert-manager/cert-manager/releases/download/v1.7.1/cmctl-$OS-$ARCH.tar.gz
tar xzf cmctl-$OS-$ARCH.tar.gz
sudo mv cmctl /usr/local/bin

cmctl completion bash >$(brew --prefix)/etc/bash_completion.d/cmctl
```

## environment variables

```sh
```

## option

```sh
```

## usage

```sh
cmctl check api
```

## see also

- [[kubectl]]
- [[k3s]]
- [[go]]
- [[openssl]]

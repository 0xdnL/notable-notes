---
tags: [container]
title: kind
created: '2021-11-29T09:47:11.585Z'
modified: '2023-11-08T14:33:37.614Z'
---

# kind

> run local kubernetes clusters using [[docker]] container "nodes"

## install

```sh
brew install kind
```

## usage

```sh
kind create cluster --image=kindest/node:v1.22.4 --config CONFIG.yaml
kind create cluster --name kind-2

kind get clusters

kind delete cluster --name NAME
 
kind load docker-image my-custom-image-0 my-custom-image-1 --name NAME    # images can be loaded into your cluster nodes
```

## see also

- [[k3s]], [[k3d]]
- [[rdctl]]
- [[flux]]
- [[kubectl]]
- [[minikube]]
- [[docker]]
- [kind.sigs.k8s.io/](https://kind.sigs.k8s.io/)

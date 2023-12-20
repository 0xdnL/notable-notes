---
tags: [container]
title: flux
created: '2022-01-17T13:49:51.051Z'
modified: '2023-11-24T08:31:50.562Z'
---

# flux

> tool for keeping Kubernetes clusters in sync with sources of configuration, and automating updates to configuration when there is new code to deploy

## install

```sh
brew install fluxcd/tap/flux
```

## usage

```sh
flux check --pre

flux bootstrap gitlab \
  --token-auth \
  --hostname=$GITLAB_HOST \
  --owner=$GITLAB_USER \
  --repository=flux-playground \
  --branch=develop \
  --path=clusters/kind-cluster \
  --author-email $AUTHOR_MAIL \
  --author-name $AUTHOR_NAME

flux get kustomizations --watch
```

## see also

- [[kubectl]]
- [[gitops]]
- [[argocd]]
- [fluxcd.io/docs](https://fluxcd.io/docs/)

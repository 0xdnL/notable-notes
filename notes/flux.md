---
tags: [container]
title: flux
created: '2022-01-17T13:49:51.051Z'
modified: '2025-11-14T10:25:39.634Z'
---

# flux

> tool for keeping Kubernetes clusters in sync with sources of configuration, and automating updates to configuration when there is new code to deploy

[[gitops]], [[argocd]]

## install

```sh
brew install fluxcd/tap/flux


curl -LO https://github.com/fluxcd/flux2/releases/download/v0.41.2/flux_0.41.2_darwin_arm64.tar.gz
```

[[brew]]

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

flux get hr HELMRELEASE -n NS

flux suspend hr HELMRELEASE -n NS

flux resume hr HELMRELEASE -n NS

flux reconcile source git flux-system

flux tree kustomization flux-system

flux logs --all-namespaces --level=error
```

## kubectl

```sh
kubectl get kustomizations.kustomize.toolkit.fluxcd.io/flux-system -o yaml | yq '.status.inventory'

kubectl get helmreleases.helm.toolkit.fluxcd.io loki -n  monitoring -o yaml
```

[[kubectl]]

## see also

- [[helm]], [[kustomize]]
- [[kubeseal]]
- [fluxcd.io/docs](https://fluxcd.io/docs/)

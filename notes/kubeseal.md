---
tags: [container]
title: kubeseal
created: '2020-11-05T12:49:58.867Z'
modified: '2021-10-29T12:39:49.027Z'
---

# kubeseal

> `SealedSecrets` are composed of  a cluster-side controller / operator and a client-side utility: `kubeseal`
> `kubeseal` utility uses asymmetric crypto to encrypt secrets that only the controller can decrypt


## install

`brew install kuebseal`

## usage

```sh
kubeseal
```

## see also

- [[kubectl]]
- [[kustomize]]
- [github.com/bitnami-labs/sealed-secrets](https://github.com/bitnami-labs/sealed-secrets)
- [[openssl]]

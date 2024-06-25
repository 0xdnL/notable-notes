---
tags: [container]
title: kubeseal
created: '2020-11-05T12:49:58.867Z'
modified: '2024-01-03T07:30:44.010Z'
---

# kubeseal

> `SealedSecrets` are composed of  a cluster-side controller / operator and a client-side utility: `kubeseal`
> `kubeseal` utility uses asymmetric crypto to encrypt secrets that only the controller can decrypt


## install

```sh
brew install kuebseal
```

## usage

```sh
kubeseal

kubectl get service sealed-secrets-controller -n kube-system

kubeseal --controller-name sealed-secrets ARGS

kubeseal --scope cluster-wide <secret.yaml >sealed-secret.json


kubeseal --fetch-cert --controller-namespace=flux-system --controller-name=sealed-secrets > sealed-secret-pub.crt

kubeseal --format=yaml --cert=sealed-secret-pub.crt < secret.yaml > secret-enc.yaml
```

## example

```
echo -n bar | kubectl create secret generic mysecret --dry-run=client --from-file=foo=/dev/stdin -o json >mysecret.json

kubeseal -f mysecret.json -w mysealedsecret.json

kubectl create -f mysealedsecret.json
kubectl get secret mysecret
```

## see also

- [[kubectl]]
- [[kustomize]]
- [github.com/bitnami-labs/sealed-secrets](https://github.com/bitnami-labs/sealed-secrets)
- [[openssl]]

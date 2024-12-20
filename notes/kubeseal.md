---
tags: [container]
title: kubeseal
created: '2020-11-05T12:49:58.867Z'
modified: '2024-12-18T11:57:27.424Z'
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

```sh
kubectl create secret generic SECRET_NAME \
  --from-literal=AWS_ACCESS_KEY_ID=AWS_ACCESS_KEY_ID \
  --from-literal=AWS_SECRET_ACCESS_KEY=AWS_SECRET_ACCESS_KEY \
  --dry-run=client \
  -o yaml > SECRET.yaml

kubeseal -v=8 \
  --format=yaml \
  --cert=../sealed-secret-pub.crt \
  --controller-name=sealed-secrets < SECRET.yaml > SECRET-enc.yaml
```

[[bash redirects]]

## see also

- [[kubectl]]
- [[kustomize]]
- [github.com/bitnami-labs/sealed-secrets](https://github.com/bitnami-labs/sealed-secrets)
- [[openssl]]

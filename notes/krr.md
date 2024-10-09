---
tags: [container]
title: krr
created: '2024-07-30T22:37:20.028Z'
modified: '2024-10-08T09:22:15.731Z'
---

# krr

> Robusta KRR (Kubernetes Resource Recommender) - athers pod usage data from Prometheus and recommends requests and limits for CPU and memory

## install

```sh
brew tap robusta-dev/homebrew-krr
brew install krr
```

## usage

```sh
krr simple

krr simple -n default -n ingress-nginx    # run on namespaces

krr simple -n monitoring -p http://127.0.0.1:9090 --quiet --width 400     # port-forwarded prometheus
```

## see also

- [[kubectl]]

---
title: kubeadm
created: '2025-04-27T11:06:14.463Z'
modified: '2025-04-28T05:51:31.248Z'
---

# kubeadm

> bootstrap a secure kubernetes cluster

[[k3s]]

## install

```sh
curl -LO https://dl.k8s.io/release/v1.30.12/bin/linux/amd64/kubeadm
chmod +x kubeadm && mv kubeadm /usr/local/bin
```

## usage

```sh
kubeadm config images list
kubeadm config images pull
```

## see also

- [[sysctl]]
- [[systemctl]]
- [[kubectl]]

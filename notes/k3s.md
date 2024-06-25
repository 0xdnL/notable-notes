---
tags: [container]
title: k3s
created: '2021-10-15T07:36:40.840Z'
modified: '2024-03-23T13:27:27.145Z'
---

# k3s

> lightweight kubernetes distro aimed for developers & IoT devices

## install

```sh
curl -sfL https://get.k3s.io | sh -
```

## env

```sh
K3S_DEBUG
```

## option

```sh
          --debug                 # (logging) Turn on debug logs [$K3S_DEBUG]
-d value, --data-dir value        # (data) Folder to hold state default /var/lib/rancher/k3s or ${HOME}/.rancher/k3s if not root
-h,       --help                  # show help
-v,       --version               # print the version
```

## usage

```sh
k3s server           # Run management server
k3s agent            # Run node agent
k3s kubectl          # Run kubectl
k3s crictl           # Run crictl
k3s ctr              # Run ctr
k3s check-config     # Run config check
k3s etcd-snapshot    # Trigger an immediate etcd snapshot
k3s secrets-encrypt  # Control secrets encryption and keys rotation
k3s certificate      # Certificates management
k3s completion       # Install shell completion script
k3s help, h          # Shows a list of commands or help for one command

k3s server \
  --cluster-reset \
  --cluster-reset-restore-path=/var/lib/rancher/k3s/server/db/snapshots/etcd-snapshot-k3s-server-1-1643738640 \
  --node-external-ip 192.168.56.11 \
  --node-ip 192.168.56.11
```

## systemctl

```sh
systemctl start k3s
systemctl stop k3s

systemctl daemon-reload && systemctl restart k3s
```

[[journalctl]], [[systemctl]]

## etcd

```sh
curl -L \
  --cacert /var/lib/rancher/k3s/server/tls/etcd/server-ca.crt \
  --cert /var/lib/rancher/k3s/server/tls/etcd/server-client.crt \
  --key /var/lib/rancher/k3s/server/tls/etcd/server-client.key \
  https://127.0.0.1:2379/version
```

```sh
ETCDCTL_ENDPOINTS='https://127.0.0.1:2379' 
ETCDCTL_CACERT='/var/lib/rancher/k3s/server/tls/etcd/server-ca.crt' 
ETCDCTL_CERT='/var/lib/rancher/k3s/server/tls/etcd/server-client.crt' 
ETCDCTL_KEY='/var/lib/rancher/k3s/server/tls/etcd/server-client.key' 
ETCDCTL_API=3 

etcdctl endpoint status --cluster --write-out=table

etcdctl get /registry/clusterrolebindings/system:basic-user -w json|jq '.kvs[].key|=@base64d|.kvs[].value|=@base64d'
```

[[etcdctl]]

## see also

- [[jq]]
- [[k3d]], [[k3sup]]
- [[kubectl]], [[k9s]]
- [[k0s]], [[kind]], [[microk8s]], [[minikube]]
- [[vagrant]], [[ansible]]
- [github.com/k3s-io/k3s](https://github.com/k3s-io/k3s)


---
tags: [systemd]
title: etcdctl
created: '2019-09-24T04:24:49.035Z'
modified: '2025-04-17T08:52:23.444Z'
---

# etcdctl

> cli client for [[etcd]]

## install

```sh
brew install etcd
```

## env

```sh
ETCDCTL_API           # set api version
ETCDCTL_CACERT        # tmp/ca.pem
ETCDCTL_CERT          # tmp/cert.pem
ETCDCTL_KEY           # tmp/key.pem
ETCDCTL_ENDPOINTS     #
```

## option

```sh
    --cacert=""                              # verify certificates of TLS-enabled secure servers using this CA bundle
    --cert=""                                # identify secure client using this TLS certificate file
    --command-timeout=5s                     # timeout for short running command (excluding dial timeout)
    --debug[=false]                          # enable client-side debug logging
    --dial-timeout=2s                        # dial timeout for client connections
-d, --discovery-srv=""                       # domain name to query for SRV records describing cluster endpoints
    --discovery-srv-name=""                  # service name to query when using DNS discovery
    --endpoints=[127.0.0.1:2379]             # gRPC endpoints
-h, --help[=false]                           # help for etcdctl
    --hex[=false]                            # print byte strings as hex encoded strings
    --insecure-discovery[=true]              # accept insecure SRV records describing cluster endpoints
    --insecure-skip-tls-verify[=false]       # skip server certificate verification
    --insecure-transport[=true]              # disable transport security for client connections
    --keepalive-time=2s                      # keepalive time for client connections
    --keepalive-timeout=6s                   # keepalive timeout for client connections
    --key=""                                 # identify secure client using this TLS key file
    --password=""                            # password for authentication (if this option is used, --user option shouldn't include password)
    --user=""                                # username[:password] for authentication (prompt if password is not supplied)
-w, --write-out="simple"                     # output format: json, protobuf, simple, table
```

## api v2

```sh
export ETCDCTL_API=2
etcdctl --version
etcdctl --u "root:${ETCD_ROOT_PASSWORD}" set v2key1 v2val1
etcdctl --u "root:${ETCD_ROOT_PASSWORD}" get v2key1 v2val1

etcdctl backup
etcdctl cluster-health
etcdctl mk
etcdctl mkdir
etcdctl set
```

## api v3

```sh
export ETCDCTL_API=3
etcdctl version
etcdctl --u "root:${ETCD_ROOT_PASSWORD}" put foo "Hello World!"
etcdctl --u "root:${ETCD_ROOT_PASSWORD}" get foo

etcdctl member list
etcdctl snapshot save 
etcdctl endpoint health
etcdctl get
etcdctl put

etcdctl \
  --cacert /var/lib/rancher/k3s/server/tls/etcd/server-ca.crt \
  --cert /var/lib/rancher/k3s/server/tls/etcd/server-client.crt \
  --key /var/lib/rancher/k3s/server/tls/etcd/server-client.key \
  member list

kubectl exec etcd-master -n kube-system -- sh -c "ETCDCTL_API=3 etcdctl get / \
  --prefix \
  --keys-only \
  --limit=10 \
  --cacert /etc/kubernetes/pki/etcd/ca.crt \
  --cert /etc/kubernetes/pki/etcd/server.crt  \
  --key /etc/kubernetes/pki/etcd/server.key" 
```

[[kubectl]]

## see also

- [github.com/etcd-io/etcd/etcdctl](https://github.com/etcd-io/etcd/tree/main/etcdctl)
- [[kubeadm]], [[k3s]]
- [[consul]]
- [[zookeeper-shell]]
- [[redis-cli]]
- [[raft consesus algorithm]]


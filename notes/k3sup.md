---
tags: [container]
title: k3sup
created: '2022-01-12T16:50:10.912Z'
modified: '2023-12-20T15:04:44.532Z'
---

# k3sup

## install 

```sh
curl -sLS https://get.k3sup.dev | sh && sudo install k3sup /usr/local/bin/
```


## option

```sh
-h, --help            # help for k3sup
```

## usage

```sh
k3sup completion      # Generate the autocompletion script for the specified shell
k3sup help            # Help about any command
k3sup install         # Install k3s on a server via SSH
k3sup join            # Install the k3s agent on a remote host and join it to an existing server
k3sup node-token      # Retrieve the node token from a server
k3sup plan            # Plan an installation of K3s.
k3sup ready           # Check if a cluster is ready using kubectl.
k3sup update          # Print update instructions
k3sup version         # Print the version


k3sup install \
  --ssh-key ~/.ssh/id_ed25519 \
  --ip=192.168.56.11 \
  --user=root \
  --k3s-channel=stable \
  --local-path=k3s-server-1.yaml \
  --context k3s-server-1 \
  --k3s-extra-args="--node-external-ip 192.168.56.11 --node-ip 192.168.56.11"

k3sup join \
  --ssh-key ~/.ssh/id_ed25519 \
  --ip=192.168.56.12 \
  --server-user=root \
  --server-ip=192.168.56.11 \
  --user=root \
  --k3s-channel=stable \
  --k3s-extra-args="--node-external-ip 192.168.56.12 --node-ip 192.168.56.12"


k3sup install \
  --ssh-key ~/.ssh/id_ed25519 \
  --ip=192.168.56.11 \
  --user=root \
  --k3s-channel=stable \
  --cluster `# init etcd-backend` \
  --local-path=k3s-server-1.yaml \
  --context k3s-server-1 \
  --k3s-extra-args="--node-external-ip 192.168.56.11 --node-ip 192.168.56.11"

k3sup join \
  --ssh-key ~/.ssh/id_ed25519 \
  --ip=192.168.56.12 \
  --server-user=root \
  --server-ip=192.168.56.11 \
  --user=root \
  --k3s-channel=stable \
  --server `# join etcd via server`\
  --k3s-extra-args="--node-external-ip 192.168.56.12 --node-ip 192.168.56.12"
```

## see also

- [[k3s]]
- [[kubectl]]
- [[vagrant]]

---
tags: [container]
title: ctr
created: '2020-03-12T13:48:00.174Z'
modified: '2024-10-26T16:43:43.507Z'
---

# ctr

> manage containers run with [[containerd]]

- cli based on the GRPC api

## install

```sh
curl -LO https://github.com/containerd/containerd/releases/download/v1.7.23/containerd-1.7.23-linux-amd64.tar.gz
curl -LO https://github.com/containerd/containerd/releases/download/v1.7.23/containerd-1.7.23-linux-amd64.tar.gz.sha256sum
cat containerd-1.7.23-linux-amd64.tar.gz.sha256sum | sha256sum --check
tar Cxzvf /usr/local containerd-1.7.23-linux-amd64.tar.gz

# start containerd via systemd
curl -LO https://raw.githubusercontent.com/containerd/containerd/main/containerd.service
mv containerd.service /etc/systemd/system
systemctl daemon-reload
systemctl enable --now containerd
```

## environment

```sh
CONTAINERD_ADDRESS      # containerd's GRPC server address
CONTAINERD_NAMESPACE    # namespace to use
```

## option

```sh
          --debug                      # enable debug output in logs
-a value, --address value              # containerd's GRPC server address, default: /run/containerd/containerd.sock
          --timeout value              # total timeout for ctr commands, default: 0s
          --connect-timeout value      # timeout for connecting to containerd, default: 0s
-n value, --namespace value            # namespace to use, default: "default"
-h,       --help                       # show help
-v,       --version                    # print the version
```

## plugins, plugin            

> provides information about containerd plugins

```sh
ctr
```

## version                    

> print the client and server versions

```sh
ctr
```

## containers, c, container   

> manage containers

```sh
ctr containers start redis /containers/redis

ctr -n k8s.io containers list
```

## content                    

> manage content

```sh
ctr
```

## events, event              

> display containerd events

```sh
ctr events                # get events
```

## images, image, i           

> manage images

```sh
ctr images list

ctr -n=k8s.io image export  xxx.tar  IMAGE_LIST
ctr -n=k8s.io image import  xxx.tar

ctr image export /tmp/nginx.tar docker.io/library/nginx:latest          # saves image's content to tarball
mkdir /tmp/nginx_image
tar -xf /tmp/nginx.tar -C /tmp/nginx_image/                             # extract raw image layers

mkdir /tmp/nginx_rootfs
ctr image mount docker.io/library/nginx:latest /tmp/nginx_rootfs   # mount image to explore its root filesystem
ls -l /tmp/nginx_rootfs/                                           # view image root fs
ctr image unmount /tmp/nginx_rootfs                                # unmount image
```

## leases                     

> manage leases

```sh
ctr
```

## namespaces, namespace, ns  

> manage namespaces

```sh
ctr
```

## pprof                      

> provide golang pprof outputs for containerd

```sh
ctr
```

## run                        

> run a container

```sh
ctr
```

## snapshots, snapshot        

> manage snapshots

```sh
ctr
```

## tasks, t, task             

> manage tasks

```sh
ctr tasks
```

## install                    

> install a new package

```sh
ctr
```

## oci                        

> OCI tools

```sh
ctr
```

## shim                       

> interact with a shim directly

```sh
ctr shim
```

## help, h

> Shows a list of commands or help for one command

```sh
ctr help
```

## see also

- [[runc]]
- [[docker]], [[containerd]]
- [[linuxkit]]
- [[crictl]], [[kubectl]]
- [github.com/projectatomic/containerd/cli](https://github.com/projectatomic/containerd/blob/master/docs/cli.md)


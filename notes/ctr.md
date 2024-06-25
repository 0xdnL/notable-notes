---
tags: [container]
title: ctr
created: '2020-03-12T13:48:00.174Z'
modified: '2024-04-15T12:19:40.188Z'
---

# ctr

> default cli based on the GRPC api - create and manage containers run with [[containerd]]

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
ctr
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
ctr
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
ctr
```

   help, h                    Shows a list of commands or help for one command


## see also

- [github.com/projectatomic/containerd/cli](https://github.com/projectatomic/containerd/blob/master/docs/cli.md)
- [[containerd]]
- [[linuxkit]]
- [[docker]]
- [[crictl]]
- [[k3s]], [[kubectl]]

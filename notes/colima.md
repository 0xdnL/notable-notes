---
tags: [container, linux, macos, virtualization]
title: colima
created: '2023-05-30T07:23:59.486Z'
modified: '2024-11-28T11:54:11.708Z'
---

# colima

> containers in [[lim]] - container runtimes on macoss (and Linux) with minimal setup

## install

```sh
brew install colima

brew services start colima    # start colima now and restart at login

sudo ln ~/.colima/default/docker.sock /var/run    # for apps not respecting docker context
ls /var/run                                       # we can verify docker.sock is now in the directory
```

## option

```sh
-h, --help                # help for colima
-p, --profile PROFILE     # profile name, for multiple instances (default "default")
-v, --verbose             # enable verbose log
    --version             # version for colima
    --very-verbose        # enable more verbose log
```

## start

> start colima with the specified container runtime and optional kubernetes

```sh
    --activate                    # set as active Docker/Kubernetes context on startup (default true)
-a, --arch string                 # architecture (aarch64, x86_64) (default "aarch64")
-c, --cpu int                     # number of CPUs (default 2)
    --cpu-type string             # the CPU type, options can be checked with 'qemu-system-aarch64 -cpu help'
-d, --disk int                    # disk size in GiB (default 100)
-n, --dns ipSlice                 # DNS resolvers for the VM (default [])
    --dns-host strings            # custom DNS names to provide to resolver
-e, --edit                        # edit the configuration file before starting
    --editor string               # editor to use for edit e.g. vim, nano, code (default "$EDITOR" env var)
    --env stringToString          # environment variables for the VM (default [])
-f, --foreground                  # Keep colima in the foreground
-h, --help                        # help for start
    --hostname string             # custom hostname for the virtual machine
    --k3s-arg strings             # additional args to pass to k3s (default [--disable=traefik])
-k, --kubernetes                  # start with Kubernetes
    --kubernetes-version string   # must match a k3s version https://github.com/k3s-io/k3s/releases (default "v1.31.2+k3s1")
-m, --memory int                  # memory in GiB (default 2)
-V, --mount strings               # directories to mount, suffix ':w' for writable
    --mount-inotify               # propagate inotify file events to the VM (default true)
    --mount-type string           # volume driver for the mount (sshfs, 9p, virtiofs) (default "sshfs")
    --network-address             # assign reachable IP address to the VM
    --network-host-addresses      # support port forwarding to specific host IP addresses
-r, --runtime string              # container runtime (containerd, docker, incus) (default "docker")
    --save-config                 # persist and overwrite config file with (newly) specified flags (default true)
-s, --ssh-agent                   # forward SSH agent to the VM
    --ssh-config                  # generate SSH config in ~/.ssh/config (default true)
    --ssh-port int                # SSH server port
-t, --vm-type string              # virtual machine type (qemu, vz) (default "qemu")
    --vz-rosetta                  # enable Rosetta for amd64 emulation
```

```sh
colima start
colima start --edit     # customize before startup
colima start --foreground
colima start --runtime containerd
colima start --kubernetes
colima start --runtime containerd --kubernetes
colima start --cpu 4 --memory 8 --disk 100
colima start --arch aarch64
colima start --dns 1.1.1.1 --dns 8.8.8.8
colima start --dns-host example.com=1.2.3.4
colima start --kubernetes --k3s-arg=--disable=coredns,servicelb,traefik,local-storage,metrics-server

#      --network-address             assign reachable IP address to the VM
#      --network-host-addresses      support port forwarding to specific host IP addresses

colima start --network-address
colima start -f           # start, but not as background service
colima start --arch x86_64 --cpu 4 --memory 16
```

## usage

```sh
colima completion         # generate completion script
colima delete             # delete and teardown Colima
colima help               # help about any command
colima kubernetes         # manage Kubernetes cluster
colima list               # list instances
colima nerdctl            # run nerdctl (requires containerd runtime)
colima restart            # restart Colima
colima ssh                # SSH into the VM
colima ssh-config         # show SSH connection config


colima status             # show the status of Colima

colima stop               # stop Colima
colima template           # edit the template for default configurations
colima version            # print the version of Colima
```

## see also

- [[lima]]
- [[qemu]]
- [[docker]]
- [[nerdctl]]
- [github.com/abiosoft/colima](https://github.com/abiosoft/colima)

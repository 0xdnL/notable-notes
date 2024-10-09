---
tags: [container]
title: podman
created: '2021-09-06T12:17:24.319Z'
modified: '2024-09-30T11:04:33.214Z'
---

# podman

> manage pods, containers and images

## install

```sh
brew install podman
```

## env

```sh
CONTAINER_CONNECTION
CONTAINER_SSHKEY
CONTAINER_HOST
```

## option

```sh
    --config string             # Location of authentication config file
-c, --connection string         # Connection to use for remote Podman service (CONTAINER_CONNECTION)
    --help                      # Help for podman
    --identity string           # path to SSH identity file, (CONTAINER_SSHKEY)
    --log-level string          # Log messages above specified level (trace, debug, info, warn, warning, error, fatal, panic) (default "warn")
    --out string                # Send output (stdout) from podman to a file
    --ssh string                # define the ssh mode (default "golang")
    --storage-opt stringArray   # Used to pass an option to the storage driver
    --url string                # URL to access Podman service (CONTAINER_HOST) (default "unix:///var/path/to/podman podman.sock")
-v, --version                   # version for podman
```

## usage

```sh
podman machine init

podman machine start

podman machine list

podman machine ssh

podman build -t TAG .

podman run -ti --rm IMAGE
```

## see also

- [[docker]]
- [[colima]]
- [[skopeo]]
- [[crc]]

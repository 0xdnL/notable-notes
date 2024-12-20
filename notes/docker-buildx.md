---
title: docker-buildx
created: '2024-11-16T05:27:55.113Z'
modified: '2024-11-16T05:30:04.461Z'
---

# docker-buildx

> extends build capabilities for [[docker]] with BuildKit

## install

bundled with [[rdctl]]

## option

```sh
    --builder string   # override the configured builder instance
-D, --debug            # enable debug logging
-h, --help             # help for docker-buildx
```

## usage

```sh
docker-buildx bake        # build from a file
docker-buildx build       # Start a build
docker-buildx create      # Create a new builder instance
docker-buildx dial-stdio  # Proxy current stdio streams to builder instance
docker-buildx du          # Disk usage
docker-buildx help        # Help about any command
docker-buildx imagetools  # Commands to work on images in registry
docker-buildx inspect     # Inspect current builder instance
docker-buildx ls          # List builder instances
docker-buildx prune       # Remove build cache
docker-buildx rm          # Remove one or more builder instances
docker-buildx stop        # Stop builder instance
docker-buildx use         # Set the current builder instance
docker-buildx version     # Show buildx version information
```

## see also

- [[docker]]
- [[kaniko]]

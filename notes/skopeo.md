---
tags: [container]
title: skopeo
created: '2021-10-19T11:25:30.764Z'
modified: '2024-06-05T09:02:07.701Z'
---

# skopeo

> performs various operations on container images and image repositories

## install

```sh
brew install skopeo
```

## usage

```sh
skopeo login quay.io --username USERNAME

skopeo inspect docker://quay.io/PATH/IMAGE:TAG
```

## see also

- [[dive]]
- [[podman]]
- [[buildah]]
- [[crictl]]
- [[crane]]
- [[pack]]

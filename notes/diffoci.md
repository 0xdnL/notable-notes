---
tags: [go]
title: diffoci
created: '2024-12-05T15:59:29.250Z'
modified: '2024-12-05T16:02:02.578Z'
---

# diffoci

> compares [[docker]] and OCI container images for helping [reproducible builds](https://reproducible-builds.org/)

[github.com/reproducible-containers/diffoci](https://github.com/reproducible-containers/diffoci)

## install

```sh
go install github.com/reproducible-containers/diffoci/cmd/diffoci@latest
```

## usage

```sh
diffoci diff docker://golang:1.21-alpine3.18 docker://my-golang-1.21-alpine3.18 --semantic --report-dir=~/diff
```

## see also

- [[dive]]

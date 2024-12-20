---
tags: [container, linux, packagemanager, shell]
title: apk
created: '2019-07-30T20:26:52.476Z'
modified: '2024-12-05T14:38:50.253Z'
---

# apk

> packages for `alpine linux`

digitally signed `tar.gz` archives containing programs, configuration files, and dependency metadata
have the extension `.apk`, and are often called `"a-packs"`

## usage

```sh
apk info    # list installed

apk add --no-cache package  # install package

apk add --update py-pip

apk del pkg

# unsatisfiable constraints
#  if package is only available in edge alpine repo, not in a stable one
echo "http://dl-cdn.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories
```

## see also

- [[busybox]]
- [[apt]], [[apt-get]]
- [wiki.alpinelinux.org](https://wiki.alpinelinux.org/wiki/Alpine_Linux_package_management)
- [docker-alpine :: viewdocs.io](http://gliderlabs.viewdocs.io/docker-alpine/)
- [BusyBox - The Swiss Army Knife of Embedded Linux](https://busybox.net/downloads/BusyBox.html)
- [ERROR: unsatisfiable constraints using apk in dockerfile - Stack Overflow](https://stackoverflow.com/a/48893148)



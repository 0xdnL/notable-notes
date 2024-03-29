---
tags: [linux, packagemanager]
title: yum
created: '2019-07-30T20:38:53.233Z'
modified: '2023-03-14T11:29:09.820Z'
---

# yum

> `yellowdog updater, modified`

## usage

```sh
yum install -y package

yum install -q package

yum remove pkg


yum provides $(which ip)        # find out package

yum whatprovides */mkpasswd     # find out package


yum makecache fast  # Download yum repository data to cache

yum list installed

yum list available

yum repolist
```

## see also

- [[rpm]]
- [[tdnf]]
- [[microdnf]]
- [redhat.com/yum-cheat-sheet](https://access.redhat.com/articles/yum-cheat-sheet)
- [[apt-get]]
- [[aws]]
- [[amazon-linux-extras]]

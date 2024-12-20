---
tags: [linux]
title: apt-cache
created: '2019-11-28T11:57:30.886Z'
modified: '2024-12-05T14:36:28.577Z'
---

# apt-cache

> performs a variety of operations on apt's package cache - does not manipulate the state of the system

## search

```sh
apt-cache search REGEX    # full text search on available package lists; searches package names and descriptions         
                          # --full          output identical to show is produced for each matched package
                          # --names-only    long description is not searched, only the package name

apt-cache search lint

apt-cache search $i | grep -E "^$i\s"
```

## madison

```sh
apt-cache madison PACKAGE    # displays available versions of a package in a tabular format

apt-cache madison rabbitmq-server
```

## usage

```sh
apt-cache showpkg    # showpkg displays information about the packages

apt-cache policy     # meant to help debug issues relating to the preferences file
```

## see also

- [[apt]]
- [[apt-get]]

---
tags: [linux, packagemanager]
title: apt-get
created: '2021-10-29T12:42:44.200Z'
modified: '2023-10-14T09:54:55.253Z'
---

# apt-get

> apt package handling utility

## usage

```sh
apt-get update

apt-get upgrade         # install the newest versions of all packages

apt-get dist-upgrade    # addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions

apt-get install PACKAGE


apt-get upgrade       # will not change what is installed (only versions),
apt-get dist-upgrade  # will install or remove packages as necessary to complete the upgrade
```

## see also

- [[sudo]]
- [[systemctl]]
- [[apt]]
- [[apt-key]]
- [[brew]]
- [[yum]]
- [[zypper]]

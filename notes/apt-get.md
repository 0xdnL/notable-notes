---
tags: [linux, packagemanager]
title: apt-get
created: '2021-10-29T12:42:44.200Z'
modified: '2024-12-05T14:58:23.408Z'
---

# apt-get

> apt package handling utility

[[dpkg]],[[apt-key]], [[apt-cache]], [[apt]]

## env

```sh
DEBIAN_FRONTEND=noninteractive
```

## option

```sh
-y, --yes, --assume-yes  # automatic yes to prompts; assume "yes" as answer to all prompts and run non-interactively
```

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
- [[brew]]
- [[apk]], [[yum]], [[zypper]]

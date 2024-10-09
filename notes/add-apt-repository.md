---
tags: [linux]
title: add-apt-repository
created: '2022-02-02T09:05:29.982Z'
modified: '2024-09-22T11:15:40.869Z'
---

# add-apt-repository

> script which adds an external [[apt]] repository to either `/etc/apt/sources.list` 
> or a file in `/etc/apt/sources.list.d/` 
> or removes an already existing repository

## install

```sh
apt install software-properties-common
```

## option

```sh
-h, --help              # show help message and exit
-m, --massive-debug     # print a lot of debug information to the command line
-r, --remove            # remove the specified repository
-y, --yes               # assume yes to all queries
-k, --keyserver         # use custom keyserver instead of the default
-s, --enable-source     # allow downloading of the source packages from the repository
```

## usage

```sh
add-apt-repository "deb https://download.srcclr.com/ubuntu stable/"
add-apt-repository "ppa:ian-berke/ppa-drawers"  # ppa

add-apt-repository -r "deb https://download.srcclr.com/ubuntu stable/"
add-apt-repository -r "ppa:ian-berke/ppa-drawers"

add-apt-repository "$(wget -qO- https://packages.microsoft.com/config/ubuntu/$(lsb_release -rs)/prod.list)"
```

## see also

- [[apt-key]]
- [[apt]]
- [[apt-get]]
- [[lsb_release]]
- [[sqlcmd]]

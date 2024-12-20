---
tags: [linux, packagemanager, python]
title: apt
created: '2019-07-30T20:20:43.614Z'
modified: '2024-12-04T15:27:35.811Z'
---

# apt

> high-level commandline interface for the package management system, frontend to [[apt-get]]

[[dpkg]]

## usage

```sh
apt list --installed

apt update

apt upgrade           # will automatically install but not remove packages

apt full-upgrade      # performs the same function as apt-get dist-upgrade

apt install PKG

apt remove PKG

apt autoremove         # remove former dependencies
```

## see also

- [[sudo]]
- [[apt-get]], [[apt-key]], [[apt-file]], [[apt-cache]]
- [[journalctl]]
- [[brew]]
- [[nix]]
- [[apk]]

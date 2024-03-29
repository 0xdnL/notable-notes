---
tags: [linux]
title: lsof
created: '2019-07-30T06:19:49.166Z'
modified: '2023-04-29T17:15:11.789Z'
---

# lsof

> list open files

## install

```sh
brew    install lsof
apt-get install lsof
yum     install lsof
dnf     install lsof
apk     add     lsof
```

## option

```sh
-i :PORT        #
-P              # don't convert port-number to port-name
-w              # ignore warnings; "lsof: no pwd entry for UID 100"
```

## usage

```sh
lsof -Pi :PORT

lsof -i :80 | grep LISTEN          # lsof command find out what is using port 80

lsof -iTCP

lsof -iUDP

lsof -i4

lsof -i6
```

## see also

- [[ss]]
- [[nmap]]
- [[pmap]]
- [[mount]]
- [[bash ulimit]]
- [lsof-no-pwd-entry-for-uid](https://unix.stackexchange.com/a/193920/193945)

---
tags: [linux, network]
title: wget
created: '2019-07-30T06:19:49.266Z'
modified: '2024-10-27T07:10:11.158Z'
---

# wget

> non-interactive network downloader

## install

```
apt-get install wget
yum     install wget
brew    install wget
```

## option

```sh
-q        # no stdout
-O        # redirect output to file
-O-       # redirect output to stout, 'dash' -> stdout
```

## usage

```sh
wget -O- 10.43.135.151:9000/minio/v2/metrics/node       # print response to stdout not save to file

wget -qO- URL | CMD

wget --quiet --tries=1 --spider http://localhost/


wget -q --show-progress \
  --https-only \
  --timestamping \
  -P downloads \
  -i downloads.txt
```

## see also

- [[curl]]
- [[nc]]
- [daniel.haxx.se/docs/curl-vs-wget](https://daniel.haxx.se/docs/curl-vs-wget.html)

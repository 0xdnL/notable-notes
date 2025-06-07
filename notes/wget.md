---
tags: [linux, network]
title: wget
created: '2019-07-30T06:19:49.266Z'
modified: '2025-06-04T12:22:20.879Z'
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

 wget -S -O /dev/null http://172.51.187.134:9402/metrics    # print only headers

wget -q --show-progress \
  --https-only \
  --timestamping \
  -P downloads      `# download to dir` \
  -i downloads.txt   # download from urls in file
```

## see also

- [[curl]]
- [[nc]]
- [daniel.haxx.se/docs/curl-vs-wget](https://daniel.haxx.se/docs/curl-vs-wget.html)

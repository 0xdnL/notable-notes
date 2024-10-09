---
tags: [linux]
title: xz
created: '2024-09-29T12:33:23.455Z'
modified: '2024-10-08T09:20:37.148Z'
---

# xz

> compress or decompress FILEs in the .xz format

## install

```sh
apt-get install xz-utils          # debian/ubuntu
yum install xz                    # rehl/centos
zypper in xz                      # opensuse
pacman -S xz                      # arch linux
```

## option

```sh
-z, --compress      # force compression
-d, --decompress    # force decompression
-t, --test          # test compressed file integrity
-l, --list          # list information about .xz files
-k, --keep          # keep (don't delete) input files
-f, --force         # force overwrite of output file and (de)compress links
-c, --stdout        # write to standard output and don't delete input files
-0 ... -9           # compression preset; default is 6; take compressor *and* decompressor memory usage into account before using 7-9!
-e, --extreme       # try to improve compression ratio by using more CPU time; does not affect decompressor memory requirements
-T, --threads=NUM   # use at most NUM threads; the default is 1; set to 0 to use as many threads as there are processor cores
-q, --quiet         # suppress warnings; specify twice to suppress errors too
-v, --verbose       # be verbose; specify twice for even more verbose
-h, --help          # display this short help and exit
-H, --long-help     # display the long help (lists also the advanced options)
-V, --version       # display the version number and exit
```

## usage

```sh
file amber.tar.xz
amber.tar.xz: XZ compressed data, checksum CRC64

tar xvf amber.tar.xz
```

## see also

- [[tar]]
- [[gzip]]
- [[file]]

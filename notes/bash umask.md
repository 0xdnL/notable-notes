---
tags: [linux, shell/bash/builtin]
title: bash umask
created: '2019-07-30T06:19:49.162Z'
modified: '2021-06-07T07:04:00.000Z'
---

# bash umask

> is a builtin, that controls file creation mode mask and determins initial file-permission values
> doesnt enforce rights it forbids them !
> filter strips away permissions

## usage

```sh
OCTAL   BIN   NEG-BIN   rwx
0       000   111       rwx
1       001   110       rw-
2       010   101       r-x
3       011   100       r--
4       100   011       -wx
5       101   010       -w-
6       110   001       --x
7       111   000       ---
```

```sh
4000    = SUID = Set UserID       => -r-xr-sr-x
2000    = SGUID = Set GroupID     => -r-xr-lr-x
1000    = sticky Bit
0000    = no special modes
```

```sh
0 002

  000 000 010
  rwx rwx r-x


0 022
 
  000 010 010
  rwx r-x r-x
  
  
0 027

  000 010 111
  rwx r-x ---
```

## see also
- [[chmod]]

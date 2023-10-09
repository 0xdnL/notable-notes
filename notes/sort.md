---
tags: [coreutils]
title: sort
created: '2019-07-30T06:19:49.240Z'
modified: '2023-10-05T09:19:12.590Z'
---

# sort

> sort or merge records (lines) of text and binary files

## option

```sh
--key, -k                       #
--numeric-sort, -n              #
--general-numeric-sort, -g      #
```

## usage

```sh
sort -n -t . -k 1,1 -k 2,2 -k 3,3 -k 4,4      # sort ip via gnu sort

sort --key 3 -g                               # sort by key:3 and general numeric sort for floating point

rpm -q kernel   | sort -V                     # order by semantic version

du -d 1 -h      | sort -h                     # order by human readable output
```

## see also
- [[du]]
- [[locale]]
- [Sort IP Addresses with GNU sort](https://www.madboa.com/geek/sort-addr/)
- [stackoverflow.com/sorting-floats-with-exponents](https://stackoverflow.com/questions/10311624/sorting-floats-with-exponents-with-sort-g-bash-command)

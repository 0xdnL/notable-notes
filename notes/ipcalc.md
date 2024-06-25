---
tags: [network]
title: ipcalc
created: '2024-01-09T09:22:59.115Z'
modified: '2024-01-11T12:43:49.725Z'
---

# ipcalc

> takes ip and netmask and calculates resulting broadcast, network, host range ..

## install

```sh
brew install ipcalc
```

## option

```sh
-n, --nocolor         # Don't display ANSI color codes
-c, --color           # Display ANSI color codes (default)
-b, --nobinary        # Suppress the bitwise output
-c, --class           # Just print bit-count-mask of given address
-h, --html            # Display results as HTML (not finished in this version)
-v, --version         # Print Version
-s, --split n1 n2 n3  # Split into networks of size n1, n2, n3
-r, --range           # Deaggregate address range
  , --help            # Longer help text
```

## usage

```sh
ipcalc 192.168.0.1/24
ipcalc 192.168.0.1/255.255.128.0
ipcalc 192.168.0.1 255.255.128.0 255.255.192.0
ipcalc 192.168.0.1 0.0.63.255
```

## see also

- [[ip]]
- [jodies.de/ipcalc](http://jodies.de/ipcalc)

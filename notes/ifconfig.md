---
tags: [macos, net-tools, network]
title: ifconfig
created: '2020-01-16T07:17:37.287Z'
modified: '2023-11-28T11:45:19.989Z'
---

# ifconfig

> configure a network interface 

## install

```sh
apt install net-tools
```

## usage

```sh
ifconfig eth1 up              # activate interface eth1

ifconfig wlan0 down           # disable an active network interface

ifconfig wlan0 69.72.169.1    # assign static ip

ipconfig getifaddr en7        # get addr of interface en7
```

## see also

- [[iftop]]
- [[scutil]]
- [[nslookup]]
- [[ip]]
- [[netstat]] `netstat -i`

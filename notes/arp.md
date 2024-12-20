---
tags: [linux, net-tools, network]
title: arp
created: '2019-09-03T11:30:41.018Z'
modified: '2024-10-26T09:44:49.265Z'
---

# arp

> manipulates or displays the kernel's ipv4 network neighbour cache. It can add entries to the table, delete one, or display the current content.

## install

```sh
apt install net-tools
```

## usage

```sh
nmap -T4 -F 192.168.178.0/24    # mac adress is added to arp table only after something was sent to machine

arp -a    # display (all) hosts in alternative (BSD) style

arp -a | awk '{ ahost=$1; aip=$2; gsub("()","",aip); print aip }'

arp -a | awk '{ gsub(/[()]/,""); print $1 " " $2}'        


arp -e    # display (all) hosts in default (Linux) style

arp -a 159.254.171.22

arp -i ens192   # display for interface


cat /proc/net/arp
```

## see also

- [[nmap]]
- [[arp-scan]], [[arping]]
- [[procfs]]
- [[ip]]
- [[net-tools vs iproute]]
- [omputerhope.com/unix/arp](https://www.computerhope.com/unix/arp.htm)
- [superuser.com/questions/1272010/where-is-the-arp-cache-on-linux](https://superuser.com/questions/1272010/where-is-the-arp-cache-on-linux)

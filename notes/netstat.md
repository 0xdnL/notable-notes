---
tags: [net-tools, network]
title: netstat
created: '2019-08-28T22:19:06.348Z'
modified: '2023-11-18T12:28:37.492Z'
---

# netstat

> show network status

## install

```
apt-get install net-tools
yum     install net-tools
zypper  install net-tools
pacman  -S      netstat-nat
```

## option

```sh
-l, --listening     # show only listening sockets.  (These are omitted by default.)
-p, --program       # show the PID and name of the program to which each socket belongs
-t, --tcp           # TCP  sockets
-u, --udp           # UDP  sockets
-w                  # Raw  sockets
-x                  # Unix sockets
-n, --numeric       # show numerical addresses instead of trying to determine symbolic host, port or user names
-a, --all           # 
```

## usage

```sh
netstat -c              # continuasly
netstat -s              # summary
netstat -i              # show interfaces
netstat -st             # summary of tcp

netstat -tulpn          # `tulp'n` 🌷
netstat -tunapl         # `tuna please` 🐟
netstat -ant            # 🐜
```

## see also

- [[ifconfig]]
- [[ss]]
- [[ip]]
- [[nc]]
- [[net-tools vs iproute]]
- [[firewall-cmd]]
- [[busybox]]
- [[unix socket]]

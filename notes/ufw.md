---
tags: [linux]
title: ufw
created: '2024-03-23T13:23:02.476Z'
modified: '2024-10-08T09:20:37.169Z'
---

# ufw

> managing a netfilter firewall

## option

```sh
    --version   # show program's version number and exit
-h, --help      # show help message and exit
    --dry-run   # don't modify anything, just show the changes
```

## usage

```sh
ufw [enable|disable|reload]

ufw --dry-run default [allow|deny|reject] [incoming|outgoing|routed]

ufw --dry-run logging [on|off|LEVEL]

ufw --dry-run reset

ufw --dry-run status [verbose|numbered]

ufw --dry-run show REPORT
```

## see also

- [[kubectl]], [[k3s]]
- [[iptables]]

---
tags: [dns, macos]
title: scutil
created: '2019-07-30T06:19:49.202Z'
modified: '2025-12-06T21:38:54.483Z'
---

# scutil

> manage system configuration parameters on macos

## usage

```sh
scutil --dns          # show DNS configuration
scutil --dns          # same as cat /etc/resolv.conf
grep nameserver <(scutil --dns)     # list dns cache

tail -f /private/var/log/system.log

sudo killall -INFO mDNSResponder

scutil --prefs [preference-file]   # interactive access to the [raw] stored preferences.

scutil [-W] -r nodename
scutil [-W] -r address
scutil [-W] -r local-address remote-address
        check reachability of node, address, or address pair (-W to "watch").

scutil -w dynamic-store-key [ -t timeout ]
#        -w      wait for presense of dynamic store key
#        -t      time to wait for key

scutil --get pref         # display (or set) the specified preference
scutil --get filename path key
scutil --get HostName
scutil --get LocalHostName
scutil --get ComputerName

scutil --set pref [newval]          # New preference value to be set, If not specified, value will be read from standard input
scutil --get HostName mbp-1619
scutil --get LocalHostName mbp-1619
scutil --get ComputerName mbp-1619


scutil --proxy        # show "proxy" configuration.
scutil --nwi          # show network information
scutil --nc           # show VPN network configuration information. Use --nc help for full command list

scutil --renew [interface-name]               # re-evaluate network configuration on the interface.
scutil --allow-new-interfaces [off|on]        # manage new interface creation with screen locked.
scutil --error err#                           # display a descriptive message for the given error code
```

## see also

- [[hostname]]
- [[ifconfig]]
- [[killall]]
- [how-to-view-dns-cache-in-osx](https://stackoverflow.com/a/38882447/2087704)

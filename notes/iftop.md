---
tags: [network]
title: iftop
created: '2023-11-28T11:45:22.989Z'
modified: '2024-01-11T12:43:44.792Z'
---

# iftop

> display bandwidth usage on an interface by host

## option

```sh
-h                    # print a summary of usage
-n                    # don't do hostname lookups
-N                    # do not resolve port number to service names
-p                    # run in promiscuous mode, so that traffic which does not pass directly through the specified interface is also counted
-P                    # turn on port display
-l                    # display and count datagrams addressed to or from link-local IPv6 addresses  The default is not to display that address category
-b                    # don't display bar graphs of traffic
-m limit              # set the upper limit for the bandwidth scale  Specified as a number with a 'K', 'M' or 'G' suffix
-B                    # display bandwidth rates in bytes/sec rather than bits/sec
-i interface          # listen to packets on interface
-f filter code        # use filter code to select the packets to count Only IP packets are ever counted, so the specified code is evaluated as (filter code) and ip
-F net/mask           # specifies IPv4 network for traffic analysis  e.g. /24
-G net6/mask6         # specifies IPv6 network for traffic analysis The value of mask6 can be given as a prefix length or as a numerical address string for more compound bitmasking
-c config file        # specifies alternate config file  If not specified, iftop will use ~/iftoprc if it exists  See below for a description of config files
-t text output mode   # use text interface without ncurses and print the output to STDOUT
```

## usage

```sh
iftop
```

## see also

- [[top]], [[htop]]

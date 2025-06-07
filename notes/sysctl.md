---
tags: [linux, macos]
title: sysctl
created: '2019-07-30T06:19:49.249Z'
modified: '2025-04-28T05:53:04.465Z'
---

# sysctl 

> configure kernel parameters at runtime 

## config files

```sh
/etc/sysctl.conf             # where sysctl values are loaded at boot time, modify for permanent change
/etc/sysctl.d/k8s.conf       # custom conf
/proc/sys/vm/swappiness      # same single value
```

## usage

```sh
sysctl -a                             # print all
sysctl -n, --values                   # print only values of a variables

sysctl vm.swappiness                  # get single value
sysctl net.ipv4.ip_forward            # get single value

sysctl -n machdep.cpu.brand_string    # get cpu infor on macos: "Intel(R) Core(TM) i7-4980HQ CPU @ 2.80GHz"

sysctl –w VAR_NAME=VALUE              # modify kernel parameter temporarily
sysctl -w fs.file-max=500000          # increase open file limit to 500000
sysctl -w vm.max_map_count=262144

sysctl -p, --load[=<file>]    # read values from file
```

## see also

- [[procps]]
- [[bash ulimit]]
- [[dmesg]]
- [[launchctl]], [[systemctl]]
- [[kubeadm]], [[containerd]]

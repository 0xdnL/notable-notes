---
title: pvesh
created: '2024-10-26T09:17:17.903Z'
modified: '2024-10-26T09:20:29.793Z'
---

# pvesh

> cli for the proxmoxVE "virtual environment" API

## usage

```sh
pvesh get /nodes                          # get list of nodes in cluster
pvesh get /cluster/nextid                 # get the next id after current vm

pvesh usage cluster/options -v            # get list of available options for datacenter

pvesh set cluster/options -console html5  # set HTMl5 NoVNC console as the default console for datacenter
```

## see also

- [[qm]], [[qemu]]
- [[vboxmanage]]

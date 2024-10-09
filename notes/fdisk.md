---
tags: [filesystem, linux]
title: fdisk
created: '2019-09-02T04:54:15.186Z'
modified: '2024-10-07T17:38:15.844Z'
---

# fdisk

> partition table manipulator for linux 

## usage

```sh
fdisk -l              # lists the partitions on your system.

fdisk -l /dev/sda     # only list partitions on the first disk

fdisk /dev/sda        # enter command mode
```

## see also

- [[mdadm]]
- [[mkfs]], [[btrfs]]
- [[fsck]]
- [[filesystem]]
- [[cryptsetup]]

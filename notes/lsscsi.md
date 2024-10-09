---
tags: [linux]
title: lsscsi
created: '2024-06-26T05:54:37.071Z'
modified: '2024-10-08T09:23:35.108Z'
---

# lsscsi

> lists information about SCSI devices

```sh
      SCSI(1:0)
           | L_____ LUN  ("Logical Unit Number")
           |
        SCSI-ID  ("small computer system information")
```

## usage

```sh
lsscsi  # list all SCSI devices output format is `[h:c:t:l]` 
        # `h` is the host number
        # `c` is the channel
        # `t` is the target ID (often equivalent to the SCSI ID)
        # `l` is the LUN

[2:0:0:0]    disk    VMware   Virtual disk     2.0   /dev/sdh
[2:0:1:0]    disk    VMware   Virtual disk     2.0   /dev/sdi
[2:0:2:0]    disk    VMware   Virtual disk     2.0   /dev/sda
[2:0:3:0]    disk    VMware   Virtual disk     2.0   /dev/sdb
```


```sh
ls -ld /sys/block/sd*/device/scsi_device/*
/sys/block/sda/device/scsi_device/2:0:2:0
/sys/block/sdb/device/scsi_device/2:0:3:0
/sys/block/sdc/device/scsi_device/2:0:4:0
#                                 a:b:c:d
#                                 | | | |
#                                 | | |  d = LUN
#                                 | |  c = Device ID
#                                 |  b = SCSI channel   "Paravirtual" controller
#                                  a = Hostadapter ID   "LSI Logic"   controller

# output in the Controller:Device format:
ls -d /sys/block/sd*/device/scsi_device/* |awk -F '[:/]' '{print $4,"- SCSI",$7":"$9}'    # LSI Logic Parallel
sda - SCSI 2:2
sdb - SCSI 2:3
sdc - SCSI 2:4

ls -d /sys/block/sd*/device/scsi_device/* |awk -F '[:/]' '{print $4,"- SCSI",$8":"$9}'    # Paravirtual
sda - SCSI 0:2
sdb - SCSI 0:3
sdc - SCSI 0:4
```
[virten.net/2015/08/match-linux-scsi-devices-sdx-to-virtual-disks-in-vmware/](https://www.virten.net/2015/08/match-linux-scsi-devices-sdx-to-virtual-disks-in-vmware/)

## see also

- [[lsblk]], [[ls]]
- [[udevadm]]
- [[mount]]
- [[sg_scan sg_map]]

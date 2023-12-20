---
title: tune2fs
created: '2023-11-20T14:25:54.630Z'
modified: '2023-11-20T14:35:21.195Z'
---

# tune2fs

> used to change or modify tunable parameters on ext2, ext3 and ext4 type filesystems

## usage

```sh

tune2fs -l /dev/sdc  | grep large_dir     # check if it's enabled
tune2fs -O large_dir  /dev/sda            # enable it


tune2fs -l /dev/vdb1 | grep volume      # Display Filesystem Volume Name 

tune2fs -L Disk_One /dev/vdb1           # rename filesystem volume name

tune2fs -l /dev/vdb1 | grep volume         
tune2fs -l /dev/sda1 | grep interval     # displaying Filesystem Check Intervals and Mount Counts
tune2fs -l /dev/sda1 | grep -i count     # 

tune2fs -c -1 /dev/sda1     # Disable Filesystem Check on Boot
tune2fs -i -1 /dev/sda1     #  "-1" which disables any checking

tune2fs -c 100 -i 2m /dev/sda1    # modify the Check interval and Mount Count to only check after 100 mounts or a 2 month period
```

## see also

- [[mkfs]]

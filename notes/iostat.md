---
title: iostat
created: '2024-11-26T12:54:41.424Z'
modified: '2024-11-26T12:56:39.648Z'
---

# iostat

> report cpu and i/o statistics for devices and partitions

## install

```sh
apt-get install sysstat
```

## usage

```sh
$ iostat

Linux 5.15.0-124-generic (worker-dev-1)      26.11.2024      _x86_64_        (8 CPU)

avg-cpu:  %user   %nice %system %iowait  %steal   %idle
          24,61    0,01    5,83    0,14    0,00   69,42

Device             tps    kB_read/s    kB_wrtn/s    kB_dscd/s    kB_read    kB_wrtn    kB_dscd
sda              75,55        16,59      2594,02         0,00   21546765 3368216668          0
sdb               0,00         0,00         0,00         0,00       2729       2052          0
sdc               0,98         0,01        16,67         6,46       8010   21648588    8388612
```

## see also

- [[uptime]]
- [[lsblk]]
- [[mount]]

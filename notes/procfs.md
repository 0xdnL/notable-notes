---
tags: [filesystem, network]
title: procfs
created: '2019-09-03T11:42:10.908Z'
modified: '2025-11-24T10:02:46.747Z'
---

# procfs

> procfs or `/proc`, special linux filesystem used to present process information and kernel processes

[[procps]], [[filesystem hierarchy standard]], [[sysfs]]

## usage

```sh
/proc/self/cgroup

/proc/filesystems     # available filesystems
```

[[container]]

```sh
cat /proc/cpuinfo 
```

[[lscpu]]


```sh
cat /proc/meminfo
```

[[free]]

```sh
cat /proc/mounts

cat /proc/self/mountinfo
```

[[mount]]

## see also

- [[top]]

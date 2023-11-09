---
tags: [linux]
title: findmnt
created: '2019-10-17T05:41:04.763Z'
modified: '2023-11-08T13:18:48.327Z'
---

# findmnt

> find a filesystem 

## option

```sh
-t, --types LIST     # limit the set of filesystems by FS types
-o, --output LIST    # the output columns to be shown
```

## usage

```sh
findmnt -l            # list view 

findmnt -t nfs        # list nfs mounts

findmnt -it nfs,tmpfs,overlay,nsfs,cgroup,proc       # invert search => no nfs, tmpfs, overlay ..

findmnt -l -o target,source  
```

## see also

- [[find]]
- [[mount]]
- [[showmount]]

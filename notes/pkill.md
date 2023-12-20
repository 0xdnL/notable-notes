---
tags: [linux]
title: pkill
created: '2020-01-02T14:25:22.992Z'
modified: '2023-11-18T12:34:46.327Z'
---

# pkill

> kill signal processes by name

## option

```sh
 -f         # match against full argument lists.  The default is to match against process names
 -l         # long output.  For pgrep, print the process name in addition to the process ID for each matching process.  
            #    If used in conjunction with -f, print the process ID and the full argument list for each matching process.  
            #    For pkill, display the kill command used for each process killed.
```

## usage

```sh
pkill -fl PROCESS_NAME        # match full path

pkill -HUP sshd
```

## see also

- [[procps]]
- [[pgrep]]
- [[grep]]
- [[bash kill]], [[killall]], [[kill]]
- [[ps]]

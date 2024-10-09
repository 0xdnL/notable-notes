---
tags: [linux, macos]
title: pstree
created: '2022-11-29T08:23:13.377Z'
modified: '2024-09-09T08:25:25.103Z'
---

# pstree

> list processes as a tree

## install

```sh
brew install pstree
```

## option

```sh
-f FILE    # Read input from file instead of running “ps -kaxwwo user,pid,ppid,pgid,command”.  If file is a single dash (‘-’), pstree reads from standard input
-g N       # Use graphics chars for tree.  n = 1: IBM-850, n = 2: VT100, n = 3: UTF8
-l N       # show a maximum of N levels
-p PID     # show only parents and descendants of the process PID
-s STRING  # show only parents and descendants of processes containing the string in their commandline
-U         # Do not show branches containing only root processes
-u USER    # Show only parents and descendants of processes of user
-w         # Wide output, not truncated to terminal width
```

## usage

```sh
pstree

pstree -s $$

pstree -g 2 -s httpd    # show branches of processes containing “httpd” using VT100 graphic chars

pstree 15495            # show process number 15495 and its descendants

pstree -p 15495         # show process number 15495 and its parents and descendants
```

## see also

- [[ps]]
- [[pgrep]]
- [[initsystem]]

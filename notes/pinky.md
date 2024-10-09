---
tags: [linux]
title: pinky
created: '2024-03-01T11:30:30.866Z'
modified: '2024-10-08T09:23:35.114Z'
---

# pinky

> lightweight [[finger]] user information lookup program

## option

```sh
-l        # produce long format output for the specified USERs
-b        # omit the user's home directory and shell in long format
-h        # omit the user's project file in long format
-p        # omit the user's plan file in long format
-s        # do short format output, this is the default
-f        # omit the line of column headings in short format
-w        # omit the user's full name in short format
-i        # omit the user's full name and remote host in short format
-q        # omit the user's full name, remote host and idle time in short format
--help    # display this help and exit
--version # output version information and exit
```

## usage

```sh
pinky USER
```

## see also

- [[id]]
- [[ssh]]
- [[finger]]

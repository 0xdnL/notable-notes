---
tags: [linux]
title: nl
created: '2020-08-03T11:54:23.348Z'
modified: '2021-06-04T12:19:17.849Z'
---

# nl

> line numbering filter

## usage
```sh  
-a                # number all lines
-t                # number only nonempty lines
-n                # number no Lines
-p                # number only lines that contain a match for the basic regex
```
```sh
nl FILE                               # print file like cat with line numbers

nl -v 77 FILE                         # start with specific line number

nl -ba FILE                           # empty lines get numbered

nl -b p":[0-2]:[0-2]" /etc/passwd     # number lines that match a regex
```

## see also
- [[cat]]
- [[paste]]
- [[wc]]


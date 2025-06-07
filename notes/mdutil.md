---
tags: [macos]
title: mdutil
created: '2020-02-04T12:20:33.596Z'
modified: '2025-04-22T09:18:39.413Z'
---

# mdutil

> utility to manage macos spotlight indices

## usage

```sh
mdutil -a -i off          # disable spotlight

mdutil -a -i on           # turn on spotlight

mdutil -E /               # erase and rebuild entire spotlight-index


sudo mdutil -E /
sudo mdutil -i on /
sudo mdutil -i on /System/Volumes/Data
sudo mdutil -E /System/Volumes/Data 
```

[[sudo]]

## see also

- [[mdfind]]
- [[defaults]]
- [[macos keyboard shortcuts]]

---
tags: [coreutils, macos]
title: chmod
created: '2019-10-04T09:17:53.956Z'
modified: '2023-11-20T18:02:18.472Z'
---

# chmod

> change file modes or Access Control Lists

```sh
chmod [u|g][+|-][r|w|x]
#       |    |     ^
#       |    |     |
#       |    |     read write execute
#       |   add or remove
#     user or group

# _ rwx rwx rwx [int] owner:group
# ^               ^
# |               |
# |               number of hardlinks
# special permissions flag
#     |
#     _   no special permissions
#     d   directory
#     l   file or dir as symlink
#     s   setuid/set guid => run executable as owner with owner permissions
#     t   sticky bit
```

## usage

```sh
chmod +x FILE       # set all x flags

chmod 755 FILE
chmod 644 DIR

chmod -R 644 DIR

chmod g-w FILE      # remove write from group
chmod u+rw FILE     # give permission read, write to user

chmod a+rx FILE
```

## see also

- [[chown]]
- [[ls]]
- [[lsattr]]
- [[chattr]]
- [[filesystem]]
- [[bash umask]]

---
tags: [macos]
title: fswatch
created: '2021-10-19T10:15:19.670Z'
modified: '2023-03-25T12:32:53.495Z'
---

# fswatch

> file change monitor that receives notifications when the contents of the specified files or directories are modified

## install 

```sh
brew install fswatch
```

## usage

```sh
fswatch . | xargs -n 1 -I {} echo {}
```

## see also

- [[entr]]
- [[watch]]
- [[xargs]]
- [emcrisostomo.github.io/fswatch](https://emcrisostomo.github.io/fswatch/)

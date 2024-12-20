---
tags: [linux, macos, virtualization]
title: qemu
created: '2020-03-13T12:51:22.771Z'
modified: '2024-11-27T12:21:00.593Z'
---

# qemu

> generic and open source machine emulator and virtualizer

## install

```sh
brew install qemu
```

## usage

```sh
sudo qemu-system-x86_64 -boot d -cdrom ./boot2docker.iso -m 512
```

## see also

- [[qm]]
- [[lima]], [[colima]]
- [[podman]]
- [[vboxmanage]]
- [[vagrant]]
- [[hyperkit]]
- [qemu.org/docs](https://www.qemu.org/docs/master/system/index.html)

---
tags: [linux]
title: filesystem hierarchy standard
created: '2019-09-02T05:06:01.427Z'
modified: '2025-11-12T19:10:52.359Z'
---

# filesystem hierarchy standard

> `fhs - filesystem hierarchy standard` defines the directory structure and content in unix-like os

## path

```sh
/         # all files and directories appear under the root directory

/boot     # contains files related to the initial booting of the computer

/bin      # contains binaries usable before /usr partition is mounted. binaries used in very early boot stage or ones that you need to have available in booting single-user mode e.g. cat, ls, mount

/sbin     # similar to /bin, but contains programs that are normally run only by the system administrator/ scripts with superuser (root) privileges required
```

## `/usr`

> contains the majority of user utilities and applications

```sh
/usr/bin        # same as /bin, but for general system-wide binaries

/usr/sbin       # same as /usr/bin, but for scripts with superuser/root privileges required
```

## `/dev`

> contains entries for the physical devices that may or may not be present in the hardware

```sh
/dev/hda1   # hard drive partition containing the mounted filesystem 

/dev/loop0  # loopback devices - allows an ordinary file to be accessed as if it were a block device, enables mounting an entire filesystem within a single large file

# pseudo-devices - like a device file, but instead of acting as a bridge between os and hardware, it's a device driver without an actual device
/dev/null     # 
/dev/zero     # pseudo-device
/dev/urandom  # pseudo-device
/dev/sda1     # pseudo-device

/dev/tty1
/dev/udp      # pseudo-device
/dev/tcp      # pseudo-device
```


"shared memory" provides a temporary file storage filesystem using RAM for storing files

```sh
/dev/shm      # see also tmpfs "/tmp", docker
```

[[ipcs]], [[docker]], [datawookie.dev/../shared-memory-docker/](https://datawookie.dev/blog/2021/11/shared-memory-docker/)

```sh
/etc      # "et cetera" / "editables text config" - contains configuration files

/lib      # contains program libraries

/media    # mount point for removable media

/var      # contains variable files such as logs

/home     # home directories of users
```

```sh
/tmp      # contains temporary files
```

[[tmpfs]]

## see also

- [[filesystem]]
- [[procfs]]
- [[sysfs]]
- [[bash exec]]
- [[syscall]]

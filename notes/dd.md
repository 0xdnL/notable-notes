---
tags: [coreutils, macos]
title: dd
created: '2019-07-30T06:19:49.033Z'
modified: '2025-12-09T21:40:57.914Z'
---

# dd

> `disk dump` - convert and copy a file

[[coreutils]]

## operands

```sh
bs=n     # set input and output block size to n bytes, superseding the ibs and obs operands
ibs=n    # set input  block size to n bytes instead of the default 512
obs=n    # set output block size to n bytes instead of the default 512

cbs=n    # Set the conversion record size to n bytes, required by the record oriented conversion values

count=n  # copy only n input blocks

files=n  # copy n input files before terminating, operand is only applicable when the input device is a tape

if=file       # read input from file instead of STDIN
iflag=VALUE   # VALUE:
              # fullblock  Reading from the input file may not obtain a full block
              # direct     Set F_NOCACHE on the input file to make reads bypass any local caching

of=file       # write output to file instead of STDOUT
oflag=VALUE   # VALUE:
              #  fsync  Set the O_FSYNC flag on the output file to make writes synchronous
              #  sync   Set the O_SYNC flag on the output file to make writes synchronous, synonymous with the fsync value
              #  direct Set F_NOCACHE on the output file to make writes bypass any local caching
oflag=direct  # use direct I/O for data, allowed to make use of kernel buffering (it just causes a flush+wait for completion periodically
oflag=dsync   # use synchronized I/O for data trust that all my parameters are sensible and turn off as much kernel buffering as you can"
oflag=sync    # likewise, but also for metadata
```

## write zeros to device

```sh
dd if=/dev/zero of=/Users/user/filesize/foo.dat bs=1m count=24
# 24+0 records in
# 24+0 records out
# 25165824 bytes transferred in 0.026832 secs (937899773 bytes/sec)
```

```sh
# write zeros to /dev/mapper/backup2 encrypted device / will allocate block data with zeros
# ensures outside world will see this as random data i.e. it protect against disclosure of usage patterns:
pv -tpreb /dev/zero | dd of=/dev/mapper/backup2 bs=128M

dd if=/dev/zero of=/dev/mapper/backup2 status=progress
```

[[pv]]


## i/o performance testing

```sh
dd if=/dev/zero of=/data/$(date +"%m-%d-%y_%H-%M").test bs=1G count=1 oflag=direct
# 1+0 records in
# 1+0 records out
# 1073741824 bytes (1.1 GB, 1.0 GiB) copied, 1.94133 s, 553 MB/s
```

[thomas-krenn.com/en/wiki/Linux_I/O_Performance_Tests_using_dd](https://www.thomas-krenn.com/en/wiki/Linux_I/O_Performance_Tests_using_dd)

## flash usb drive

```sh
hdiutil convert proxmox-ve_*.iso -format UDRW -o proxmox-ve_*.dmg
diskutil list
diskutil unmountDisk /dev/diskX

dd if=proxmox-ve_*.dmg bs=1M of=/dev/rdiskX
```

[[hdiutil]], [[diskutil]], [superuser.com/why-is-dev-rdisk-about-20-times-faster-than-dev-disk-in-mac-os-x](https://superuser.com/questions/631592/why-is-dev-rdisk-about-20-times-faster-than-dev-disk-in-mac-os-x)


```sh
diskutil list
diskutil unmountDisk /dev/disk2

sudo dd if=/Users/USER/Downloads/Win11_25H2_EnglishInternational_x64.iso of=/dev/disk2 bs=1m
dd: invalid number: '1m'

sudo dd if=/Users/USER/Downloads/Win11_25H2_EnglishInternational_x64.iso of=/dev/disk2 bs=1M      # gnu version of dd

# check progress in other terminal:
sudo kill -USR1 $(pgrep ^dd$)   # linux
sudo kill -INFO $(pgrep ^dd$)   # bsd/macos
```

[[kill]]

## see also

- [[diskutil]]
- [[numfmt]]
- [[cryptsetup]]
- [rendezvouswithpavan.wordpress.com/2015/06/16/dd-bs-illegal-numeric-value-error-on-mac-os-x](https://rendezvouswithpavan.wordpress.com/2015/06/16/dd-bs-illegal-numeric-value-error-on-mac-os-x/)
- [why is dd with direct flag much slower than dsync](https://stackoverflow.com/a/50882704/2087704)

---
tags: [macos]
title: hdiutil
created: '2023-05-30T08:54:56.544Z'
modified: '2024-10-13T12:41:29.887Z'
---

# hdiutil

> manipulate disk images (attach, verify, create, etc)

## usage

```sh
hdiutil attach IMAGE.dmg                  # attach a disk image as a device

hdiutil detach /Volumes/DEVICE_NAME       # detach a disk image and terminate any associated process

hdiutil info -plist                       # display info about DiskImages.framework, disk image driver, and any images that are currently attached

hdiutil verify IMAGE.dmg                  # compute checksum of "read-only" or "compressed" image and verify it against value stored in image

hdiutil checksum IMAGE -type TYPE         # Calculate the specified checksum on the image data, regardless of image type
                                          # options: -shadow and related, -encryption, -stdinpass, -srcimagekey, -puppetstrings, and -plist.
                                          # TYPE: UDIF-CRC32 , UDIF-MD5 , CRC32 , MD5 , SHA , SHA1 , SHA256 , SHA384 , SHA512
```

## convert .iso to .dmg

```sh
hdiutil convert proxmox-ve_8.2-2.iso -format UDRW -o proxmox-ve_8.2-2.dmg
```

## install image to volume

```sh
hdiutil attach IMAGE.dmg    # mount the IMAGE.dmg to /Volumes/IMAGE

installer -package /Volumes/IMAGE/IMAGE.pkg -target /

hdiutil detach /Volumes/IMAGE   # unmount the image
```

[[imagehdiutil]], [[installer]], [apple.stackexchange.com/Is-there-a-command-to-install-a-dmg](https://apple.stackexchange.com/a/73931/394965)

## see also

- [[brew]]
- [[mount]]
- [[diskutil]]
- [[docker]]
- [[sha256sum]]
- [[rdctl]]

---
tags: [macos]
title: hdiutil
created: '2023-05-30T08:54:56.544Z'
modified: '2023-11-08T14:14:56.641Z'
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

```sh
imagehdiutil attach IMAGE.dmg    # mount the IMAGE.dmg to /Volumes/IMAGE

sudo installer -package /Volumes/IMAGE/IMAGE.pkg -target /

hdiutil detach /Volumes/IMAGE   # unmount the image
```

## see also

- [[installer]]
- [[brew]]
- [[mount]]
- [[diskutil]]
- [[docker]]
- [[sha256sum]]
- [[rdctl]]
- [apple.stackexchange.com/Is-there-a-command-to-install-a-dmg](https://apple.stackexchange.com/a/73931/394965)

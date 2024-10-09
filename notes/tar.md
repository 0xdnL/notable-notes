---
tags: [linux, macos]
title: tar
created: '2019-07-30T06:19:49.251Z'
modified: '2024-09-29T12:33:11.981Z'
---

# tar

> "tape archiver" is used to convert a group for file to an archive

`.tgz` is same as `.tar.gz`/`.tar.gzip`

## env

```sh
TAR_READER_OPTIONS  # default options for format readers and compression readers. --options option overrides this
TAR_WRITER_OPTIONS  # default options for format writers and compression writers. --options option overrides this
LANG                # locale to use.  See environ(7) for more information
TAPE                # default device.  The -f option overrides this.  Please see the description of the -f option above for more details
TZ                  # timezone to use when displaying dates.  See environ(7) for more information
```

## option

```sh
-c          # create archive
-C DIR      # changes working directory in the middle of a command line

-v          # verbose
-z          # filter the archive through gzip
-f          # archive filename
-x          # extract files from archive
-t          # list archive contents to stdout

-j          # filter the archive through bzip2
```

## usage

```sh
tar tvf archive.tar                     # listing

tar cvzf archive.tar.gzip dirname/      # create

tar cvfj archive-name.tar.bz2 dirname/  # filter archive

tar xvf archive.tar                     # extract / untar

tar ztvf archive.tar.gz    # gzipped file

tar tvf archive.tar.gz 'search-pattern'
tar tvf archive.tar.gz 'path/*/file'

tar -czf - archive | wc -c        # estimating

docker export tempconsul | tar -C ./rootfs -xf -  # change working directory and -f stdin

curl https://nodejs.org/dist/latest-../node-..-linux-x64.tar.gz | tar xz --strip-components=1
```

## show progress

```sh
tar cf - erl_crash.dump -P \
  | pv -s $(( $(du -sk erl_crash.dump | cut -f1) * 1024 )) \
  | gzip > erl_crash.dump.tar.gz

tar cf - "$1" -P | pv -s $(( $(du -sk "$1" | cut -f1) * 1024 )) \
  | gzip > "${1}.tar.gz"
```

## see also

- [[xz]]
- [[rar]]
- [[nc]]
- [[zip]]
- [[pigz unpigz]]
- [[gzip gunzip zcat]]
- [[bash redirects]]
- [gnu.org/software/tar/manual/tar](https://www.gnu.org/software/tar/manual/tar.html)
- [unix.stackexchange.com/why-would-i-tar-a-single-file](https://unix.stackexchange.com/a/277799/193945)

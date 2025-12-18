---
tags: [linux]
title: mktemp
created: '2019-11-26T08:13:04.385Z'
modified: '2025-12-18T12:35:08.309Z'
---

# mktemp

> create a temporary file or directory, safely, and print its name

[[mkdir]], [[mkfifo]]

## env

```sh
TMPDIR
```

## option

```sh
-d            # make a dir instead of a file
-q            # fail silently if an error occurs, useful if a script does not want error output to go to standard error
-t prefix     # generate  template (using the supplied prefix and TMPDIR if set) to create a filename template
-u            # Operate in ``unsafe'' mode. The temp file will be unlinked before mktemp exits. This is slightly better than mktemp(3) but still introduces a race condition. Use of this option is not encouraged
```

## usage

```sh
mktemp -d                   # make a directory instead of a file

cd $(mktemp -d)

mkdtemp -t $(basename $0)  # generate a template (using the supplied prefix and TMPDIR if set) to create a filename template.
```

```sh
trap 'rm -rf "${WORKSPACE}"' EXIT
WORKSPACE="$(mktemp --directory)"
```

```sh
SCRATCH="$(mktemp -t tmp.XXXXXXXXXX)"     # Create a temp file and store the filename in $SCRATCH
rm -f "$SCRATCH"                          # Delete the file


# create a temp file and quit if unable to get a safe temporary file
FILENAME="$(basename $0)"
TMPFILE="$(mktemp /tmp/${FILENAME}.XXXXXX)" || exit 1
echo "program output" >> $TMPFILE
```

## too few X's in template

```sh
mktemp "tmp.$(date +%Y%m%d_%H%M%S).sql"
# mktemp: too few X's in template 'tmp.20251124_164624.sql'

mktemp "tmp.$(date +%Y%m%d_%H%M%S).sql.XXX"
# tmp.20251124_164627.sql.ind
```

## see also

- [[tmpfs]]
- [[bash trap]]
- [[bash jobs]], [[bash fg]]
- [[bash pushd popd]]
- [ss64.com/osx/mktemp](https://ss64.com/osx/mktemp.html)

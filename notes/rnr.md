---
tags: [rust]
title: rnr
created: '2023-05-10T14:15:08.501Z'
modified: '2024-12-03T07:30:37.627Z'
---

# rnr

> securely rename multiple files and directories that supports regular expressions

[github.com/ismaelgv/rnr](https://github.com/ismaelgv/rnr)

## install

```sh
brew install rnr

cargo install rnr
```

## option

```sh
-b, --backup          # Generate file backups before renaming
-n, --dry-run         # Only show what would be done (default mode)
    --dump            # Force dumping operations into a file even in dry-run mode
-f, --force           # Make actual changes to files
-h, --help            # Prints help information
-x, --hidden          # Include hidden files and directories
-D, --include-dirs    # Rename matching directories
    --no-dump         # Do not dump operations into a file
-r, --recursive       # Recursive mode
-s, --silent          # Do not print any information
-V, --version         # Prints version information
```

## usage

```sh
rnr    -b -l 0 ' ' '-' SOME\ FILE\ HAVING\ -\ SPACES.ext
rnr -f -b -l 0 ' ' '_' SOME\ FILE\ HAVING\ -\ SPACES.ext
```

## see also

- [[mv]]
- [[rip]]
- [[rust]]
- [[cargo]]

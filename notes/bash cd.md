---
tags: [shell/bash/builtin]
title: bash cd
created: '2019-08-02T06:42:37.564Z'
modified: '2023-11-18T13:12:12.690Z'
---

# bash cd

> change the shell working directory

## option

```sh
-L       # force symbolic links to be followed: resolve symbolic links in DIR after processing instances of `..'
-P       # use the physical directory structure without following symbolic links: resolve symbolic links in DIR before processing instances of `..'
-e       # if the -P option is supplied, and the current working directory cannot be determined successfully, exit with a non-zero status
-@       # on systems that support it, present a file with extended attributes as a directory containing the file attributes
```

## usage

```sh
cd                    # move to homedir

cd ~                  # move to ~ expands to homedir `$HOME`

cd -                  # change to previous dir

shopt -s cdspell      # correct misspelled dir
```

## see also

- [[bash]] 
- [[bash shopt]] 
- [[bash dirs]] 
- [[bash pushd ]] 
- [[bash pwd]]
- [[bash redirects]]

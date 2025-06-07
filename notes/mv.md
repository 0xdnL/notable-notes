---
tags: [coreutils, macos]
title: mv
created: '2020-08-03T12:08:55.090Z'
modified: '2025-01-07T16:02:21.305Z'
---

# mv

> move or rename files

[[mkdir]]

## option

```sh
-f      # do not prompt for confirmation before overwriting the destination path, overrides any previous -i or -n
-h      # if the target operand is a symbolic link to a directory, do not follow it, causes the mv utility to rename the file source to the destination path target rather than moving source into the directory referenced by target.

-i      # Cause mv to write a prompt to standard error before moving a file that would overwrite an existing file.  If the response from the standard input begins with the
        character ‘y’ or ‘Y’, the move is attempted.  (The -i option overrides any previous -f or -n options.)

-n      # do not overwrite an existing file
-v      # verbose, showing files after they are moved
```

## usage

```sh
mv -f foo bar                 # rename file without confirmation

mv ~/.config/nvim{,.bak}      # rename dir using bash expansion
mv ~/.config/nvim{.bak,}    # reverse previous renaming
```

[[bash braces]] `brace expansion`

## see also

- [[rnr]]
- [[cp]], [[rm]]
- [[find]], [[rsync]]
- [[mc]], [[aws]]

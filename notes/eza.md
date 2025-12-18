---
tags: [rust]
title: eza
created: '2025-10-09T10:54:41.641Z'
modified: '2025-10-10T07:56:50.276Z'
---

# eza

> a modern replacement for [[ls]] writen in [[rust]] and forked from [[exa]]

## install

```sh
cargo install exa

brew install eza
```

[[cargo]]

## DISPLAY OPTIONS

```sh
-1, --oneline             # display one entry per line
-l, --long                # display extended file metadata as a table
-G, --grid                # display entries as a grid (default)
-x, --across              # sort the grid across, rather than downwards
-R, --recurse             # recurse into directories
-T, --tree                # recurse into directories as a tree
-X, --dereference         # dereference symbolic links when displaying information
-F, --classify=WHEN       # display type indicator by file names (always, auto, never)
    --colo[u]r=WHEN       # when to use terminal colours (always, auto, never)
    --colo[u]r-scale      # highlight levels of 'field' distinctly(all, age, size)
    --colo[u]r-scale-mode # use gradient or fixed colors in --color-scale (fixed, gradient)
    --icons=WHEN          # when to display icons (always, auto, never)
    --no-quotes           # don't quote file names with spaces
    --hyperlink           # display entries as hyperlinks
    --absolute            # display entries with their absolute path (on, follow, off)
    --follow-symlinks     # drill down into symbolic links that point to directories
-w, --width COLS          # set screen width in columns
```

## FILTERING AND SORTING OPTIONS

```sh
-a, --all                       # show hidden and 'dot' files. Use twice to also show '.' and '..' directories
-A, --almost-all                # equivalent to --all; included for compatibility with `ls -A`
-d, --treat-dirs-as-files       # list directories as files; don't list their contents
-D, --only-dirs                 # list only directories
-f, --only-files                # list only files
    --show-symlinks             # explicitly show symbolic links (for use with --only-dirs | --only-files)
    --no-symlinks               # do not show symbolic links
-L, --level DEPTH               # limit the depth of recursion
-r, --reverse                   # reverse the sort order
-s, --sort SORT_FIELD           # which field to sort by
    --group-directories-first   # list directories before other files
    --group-directories-last    # list directories after other files
-I, --ignore-glob GLOBS         # glob patterns (pipe-separated) of files to ignore
    --git-ignore                # ignore files mentioned in .gitignore
```

## usage

```sh
eza -F --color=never

eza -la

eza -a .config --tree -L 2
```

## see also

- [[ls]]
- [[procs]]
- [[rust]]

---
title: fd
created: '2024-11-21T07:54:02.573Z'
modified: '2024-11-21T08:00:04.897Z'
---

# fd

> find entries in the filesystem

alternatie to: [[find]]

## install

```sh
brew install fd
```

## options

```sh
  -H, --hidden                    # Search hidden files and directories
  -I, --no-ignore                 # Do not respect .(git|fd)ignore files
  -s, --case-sensitive            # Case-sensitive search (default: smart case)
  -i, --ignore-case               # Case-insensitive search (default: smart case)
  -g, --glob                      # Glob-based search (default: regular expression)
  -a, --absolute-path             # Show absolute instead of relative paths
  -l, --list-details              # Use a long listing format with file metadata
  -L, --follow                    # Follow symbolic links
  -p, --full-path                 # Search full abs. path (default: filename only)
  -d, --max-depth <depth>         # Set maximum search depth (default: none)
  -E, --exclude <pattern>         # Exclude entries that match the given glob pattern
  -t, --type <filetype>           # Filter by type: 
                                  #   file (f)
                                  #   directory (d/dir)
                                  #   symlink (l)
                                  #   executable (x)
                                  #   empty (e)
                                  #   socket (s)
                                  #   pipe (p)
                                  #   char-device (c)
                                  #   block-device (b)
  -e, --extension <ext>           # Filter by file extension
  -S, --size <size>               # Limit results based on the size of files
      --changed-within <date|dur> # Filter by file modification time (newer than)
      --changed-before <date|dur> # Filter by file modification time (older than)
  -o, --owner <user:group>        # Filter by owning user and/or group
      --format <fmt>              # Print results according to template
  -x, --exec <cmd>...             # Execute a command for each search result
  -X, --exec-batch <cmd>...       # Execute a command with all search results at once
  -c, --color <when>              # When to use colors [default: auto] [possible values: auto, always, never]
      --hyperlink[=<when>]        # Add hyperlinks to output paths [default: never] [possible values: auto, always, never]
  -h, --help                      # Print help (see more with '--help')
  -V, --version                   # Print version
```

## usage

```sh
fd -t f --hidden .bashrc
```

## see also

- [[nvim]], [[nvchad]]
- [[grep]], [[rg]]

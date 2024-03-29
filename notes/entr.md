---
tags: [macos]
title: entr
created: '2022-04-27T12:10:47.470Z'
modified: '2023-04-30T13:23:07.058Z'
---

# entr 

> run arbitrary commands when files change 

## install

```sh
brew install entr
```

## env

```sh
PAGER     # Set to /bin/cat by default to prevent interactive utilities from waiting for keyboard input if output does not fit on the screen
SHELL     # Specify the shell to use with the -s flag. The default is /bin/sh
EV_TRACE  # Print file system event messages
```

## option

```sh
-a    # respond to all events which occur while the utility is running. Without this option, entr consolidates events in order to avoid looping
-c    # clear the screen before invoking the utility specified on the command line. Specify twice to erase the scrollback buffer
-d    # track the directories of regular files provided as input and exit if a new file is added
      # This option also enables directories to be specified explicitly
      # If specified twice, all new entries to a directory are recognized, otherwise files with names beginning with ‘.’ are ignored
-n    # run in non-interactive mode. In this mode entr does not attempt to read from the TTY or change its properties
-p    # postpone the first execution of the utility until a file is modified
-r    # reload a persistent child process
-s    # evaluate first argument using the interpreter specified by SHELL environment variable
      # If standard output is a TTY, the name of the shell and exit code is printed after each invocation
-z    # exit after the utility completes. When combined with -r the utility will be restarted again only in response to commands or file system events
```

## usage

```sh
find . -type f -name "*.go" | entr -r go run .

while :; do
  ls -d src/*.py | entr -d ./setup.py
done
```

## see also

- [[find]]
- [[watch]]
- [[nodemon]]
- [[go]]
- [[make]]
- [eradman.com/entrproject](http://eradman.com/entrproject/)

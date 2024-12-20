---
tags: [shell]
title: sh
created: '2021-05-12T09:02:58.515Z'
modified: '2024-10-29T17:00:39.153Z'
---

# sh

> POSIX-compliant command interpreter

## environment

```sh
SHELL
PWD
HOME
```

## option

```sh
-a allexport     # export all variables assigned to
-c               # read commands from the command_string operand instead of from STDIN
-C noclobber     # don't overwrite existing files with ">"
-e errexit       # if not interactive, exit immediately if any untested command fails
-f noglob        # disable pathname expansion
-n noexec        # If not interactive, read commands but do not execute them.  This is useful for checking the syntax of shell scripts
-u nounset       # Write a message to standard error when attempting to expand a variable that is not set, and if the shell is not interactive, exit immediately
-v verbose       # The shell writes its input to standard error as it is read.  Useful for debugging
-x xtrace        # Write each command to standard error (preceded by a ‘+ ’) before it is executed.  Useful for debugging
-I ignoreeof     # Ignore EOF's from input when interactive
-i interactive   # Force the shell to behave interactively
-l               # Make dash act as if it had been invoked as a login shell
-m monitor       # Turn on job control (set automatically when interactive)
-s stdin         # read commands from STDIN
-V vi            # enable the built-in vi(1) command line editor    (disables -E if it has been set)
-E emacs         # enable the built-in emacs(1) command line editor (disables -V if it has been set)
-b notify        # enable asynchronous notification of background job completion
-p priviliged    # do not attempt to reset effective uid if it does not match uid
```

## usage

```sh
sh
```

## see also

- [[ash]]
- [[bash]]
- [[dash]]

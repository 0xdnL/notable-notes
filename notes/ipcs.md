---
title: ipcs
created: '2025-11-12T18:59:13.503Z'
modified: '2025-11-12T19:10:29.597Z'
---

# ipcs

> show information on [[ipc]] facilities

[[filesystem hierarchy standard]]

shows information on System V inter-process communication facilities. 

By default it shows information about: 

- shared memory segments
- message queues
- semaphore arrays

## install

```sh
brew install util-linux

apt-get install util-linux
```

## option

```sh
-i, --id id           # Show full details on just the one resource element identified by id. This option needs to be combined with one of the three resource options: -m, -q or -s
-h, --help            # Display help text and exit
-V, --version         # Print version and exit

# Resource options
-m, --shmems           # Write information about active shared memory segments
-q, --queues           # Write information about active message queues
-s, --semaphores       # Write information about active semaphore sets
-a, --all              # Write information about all three resources (default)

# Output formats
-c, --creator          # Show creator and owner
-l, --limits           # Show resource limits
-p, --pid              # Show PIDs of creator and last operator

-t, --time             # Write time information
-u, --summary          # Show status summary

# Representation / affect only the -l (--limits) option
-b, --bytes           # Print the sizes in bytes rather than in a human-readable format
    --human           # Print sizes in human-readable format
```

## usage


```sh
ipcs -pm      # show processes that use shared memory
```

## see also

- [[docker]]

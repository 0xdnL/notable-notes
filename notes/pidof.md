---
title: pidof
created: '2025-03-29T09:03:25.520Z'
modified: '2025-03-29T09:08:55.899Z'
---

# pidof

> find the process ID of a running program

## options

```sh
-s            # Single shot, instructs the program to only return one pid
-c            # Only return process PIDs that are running with the same root directory
-n            # Avoid stat(2) system function call on all binaries which are located on network based file systems like NFS
-q            # Do not display matched PIDs to STDOUT. Simply exit with a status of true or false to indicate whether a matching PID was found
-x            # Scripts too, causes the program to also return process id's of shells running the named scripts
-z            # Try to detect processes which are stuck in zombie (Z) status
-d SEP        # use SEP as an output separator if more than one PID is shown, default separator is a space
-o omitpid    # omit processes with that process id. The special pid %PPID can be used to name the parent process of the pidof program, in other words the calling shell or shell script
```

## usage

```sh
pidof python3

cd /proc/$(pidof python3)
```

## see also

- [[ps]]

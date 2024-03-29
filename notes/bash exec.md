---
tags: [shell/bash/builtin]
title: bash exec
created: '2019-07-30T06:19:49.006Z'
modified: '2023-11-17T12:33:54.052Z'
---

# bash exec

> execute a command that completely replaces the current process. The current shell process is destroyed, and entirely replaced by the command you specify

- replace shell with command
- shell-`PID` == command-`PID`
- `echo $$ == /proc/self`
- spawns new proc

## option

```sh
-a NAME   # pass NAME as the zeroth argument to COMMAND
-c        # execute COMMAND with an empty environment
-l        # place a dash in the zeroth argument to COMMAND
```

## usage

```sh
exec $SHELL -l    # restart shell as login

exec <FILE        # redirects stdin to a file - from that point on, all stdin comes from that file, rather than keyboard input 
                  # provides a method of reading a file line by line and possibly parsing each line of input using sed and/or awk

exec 3< FILE      # open file for reading `<` on file descriptor `3`
read -u 3 foo     # can be `read` with -u


exec >FILE        # redirects stdout to a file - sends all command output that would normally go to stdout to that file

exec N > FILE     # affects the entire script or current shell. Redirection in the PID of the script or shell from that point on has changed. 
N > FILE          # affects only the newly-forked process, not the entire script or shell


# causes file descriptor 3 to be opened for reading and writing on the specified tcp socket
# if command not specified, any redirections take effect in current shell and return status is 0
exec 3<>/dev/tcp/www.google.com/80
echo -e "GET / HTTP/1.1\r\nhost: http://www.google.com\r\nConnection: close\r\n\r\n" >&3
cat <&3
```

```sh
cat <<EOF> FILE
POST /some/pathh HTTP/1.0
User-Agent: curl/7.37.0
Host: localhost
Accept: */*
Content-Length: 7
Content-Type: application/x-www-form-urlencoded

var=val
EOF

exec 5<>/dev/tcp/www.google.com/80
cat FILE >&5
cat <&5 # reply
```

[unix.stackexchange.com/how-to-run-the-http-request-without-using-curl](https://unix.stackexchange.com/a/234089/440548)

## see also

- [[bash]]
- [[bash eval]]
- [[bash read]]
- [[filesystem hierarchy standard]]

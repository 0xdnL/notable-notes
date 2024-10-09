---
tags: [linux]
title: ps
created: '2019-07-30T06:19:49.218Z'
modified: '2024-07-09T11:53:27.727Z'
---

# ps

> prints a line of information about the current running login shell and any processes running under it

## install

```sh
apt      install procps
dnf      install procps
yum      install procps
microdnf install procps
```

## usage

```sh
ps -a           # selects all processes with a tty except session leaders

ps a --forest   # macos not supported !
ps fax

ps -C sleep

ps -u yourusername       # lists your processes


# all processes on the system
ps ax     # bsd-style
ps -e     # standard-style

# all processes on the system with UUID
ps aux    # bsd-style
ps -ef    # standard-style

#   a    show processes for all users
#   u    display the process's user/owner
#   x    also show processes not attached to a terminal


# format
ps -o KEYWORD
ps -o user,pid,time
ps -o user pid comm command

ps xawf -eo pid,user,cgroup,args

ps aux | sort -nrk 3,3 | head -n 5                      # top 5 processes
ps aux | grep apache  | awk '{print $6/1024 " MB";}'    # Ram consumption per apache process
ps aux | grep "[f]nord"                                 # don't show grep in result
```

## without ps

```sh
ls -l /proc/*/exe

for PRC in /proc/*/cmdline; { (printf "$PRC "; cat -A "$PRC") | sed 's/\^@/ /g;s|/proc/||;s|/cmdline||'; echo; }
```

## see also

- [[procs]]
- [[pgrep]]
- [[pkill]]
- [[sort]]
- [[awk]]
- [[grep]]
- [[docker]]
- [[kill]]
- [[bash kill]]
- [linuxcommand.org/lc3_man_pages/ps](http://linuxcommand.org/lc3_man_pages/ps1.html)

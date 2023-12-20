---
tags: [macos]
title: killall
created: '2023-11-18T12:30:19.156Z'
modified: '2023-11-18T12:34:13.277Z'
---

# killall

> kill processes by name

## option

```sh
-d            # be more verbose about what will be done, but do not send any signal.  The total number of user processes and the real user ID is shown.
-e            # use the effective user ID instead of the (default) real user ID for matching processes specified with the -u option.
-help         # Give a help on the command usage and exit.
-I            # Request confirmation before attempting to signal each process.
-l            # List the names of the available signals and exit, like in kill(1).
-m            # Match the argument procname as a (case sensitive) regular expression against the names of processes found.  CAUTION!  This is dangerous, a single dot will match any process running under the real UID of the caller.
-v            # Be verbose about what will be done.
-s            # Same as -v, but do not send any signal.
-SIGNAL       # Send a different signal instead of the default TERM.  The signal may be specified either as a name (with or without a leading “SIG”), or numerically.
-u user       # Limit potentially matching processes to those belonging to the specified user.
-t tty        # Limit potentially matching processes to those running on the specified tty.
-c procname   # Limit potentially matching processes to those matching the specified procname.
-q            # Suppress error message if no processes are matched.
-z            # Do not skip zombies.  This should not have any effect except to print a few error messages if there are zombie processes that match the specified pattern.
```

## usage

```sh
killall firefox               # send SIGTERM to all firefox processes
killall -u ${USER} firefox    # send SIGTERM to firefox processes belonging to USER
killall -SIGSTOP firefox      # stop all firefox processes
killall -SIGCONT firefox      # resume firefox processes
killall -s firefox            # show what would be done to firefox processes, but do not actually signal them
killall -m 'vim*'             # send SIGTERM to all processes matching provided pattern (like vim and vimdiff)
```


## see also

- [[kill]]
- [[signal]]

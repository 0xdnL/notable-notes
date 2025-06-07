---
tags: [linux, macos]
title: mkfifo
created: '2021-06-16T15:59:45.047Z'
modified: '2025-05-09T08:52:04.927Z'
---

# mkfifo

> `make fifos` aka `"named pipes"`

## usage

```sh
mkfifo PIPE_NAME          # create named pipe

mkfifo PIPE_NAME -m700    # custom permissions

ls > PIPE_NAME
cat < PIPE_NAME


ls -lart PIPE_NAME        # notice 'p' in the beginning


{ ls -l && cat FILE; } >PIPE_NAME &


ls -l >PIPE_NAME &
cat FILE >PIPE_NAME &
cat <PIPE_NAME


{ pipedata="$(<PIPE_NAME)" && echo "$pipedata"; } &
ls >PIPE_NAME 
```

## see also

- [[bash redirects]]
- [[script]]
- [[cat]]

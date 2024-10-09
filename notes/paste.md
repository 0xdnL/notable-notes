---
tags: [coreutils]
title: paste
created: '2020-08-03T11:16:34.527Z'
modified: '2024-07-15T13:45:52.452Z'
---

# paste

> merge corresponding or subsequent lines of files

## usage

```sh
paset FILE                                    # prints file like cat

ls | paste - - -                              # list files in the current directory in three columns

paste -s -d '\t\n' FILE                       # combine pairs of lines from a file into single lines

sed = FILE | paste -s -d '\t\n' - -           # number the lines in a file

find / -name bin -type d | paste -s -d : -    # colon-separated list of dirs named bin, suitable for use in the PATH environment variable

paste {fail-a,fail-b,fail-c,fail-d,fail-e}.labels | column -t # print file next to each other in column
```

## see also

- [[bash]]
- [[cat]]
- [[diff]]
- [[awk]]
- [[column]]
- [[nl]]
- [[sed]]

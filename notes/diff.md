---
tags: [linux]
title: diff
created: '2019-07-30T06:19:49.036Z'
modified: '2024-12-04T10:34:02.086Z'
---

# diff

> compare files line by line

## option

```sh
-q,     --brief                   # output only whether files differ
-i,     --ignore-case             # ignore case differences in file contents
-y,     --side-by-side            # output in two columns
-W NUM, --width=NUM               # output at most NUM (default 130) print columns
```

## usage

```sh
diff -q FILE1 FILE2                    # only output if files differ
diff -y FILE1 FILE2                    # side-by-side

diff --suppress-common-lines -y -W $(tput cols) FILE1 FILE2    # dynamic width, side-by-side

diff -y -W $(tput cols) <(CMD | jq -S) <(CMD | jq -S)

diff --unified FILE1 FILE2

diff <(sort <(md5deep -r /$1/) |cut -f1 -d' ') <(sort <(md5deep -r /$2/) |cut -f1 -d' ')

diff -y <(curl -s URL) <(cat $(brew --prefix)/PATH/git-completion.bash)
```

## see also

- [[paste]]
- [[tput]]
- [[column]]
- [[colordiff]]
- [[bash redirects]]
- [Make diff Use Full Terminal Width in Side-by-Side Mode - Unix & Linux Stack Exchange](https://unix.stackexchange.com/a/9303)

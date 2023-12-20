---
tags: [shell/bash/builtin]
title: bash shopt
created: '2019-07-30T06:19:49.237Z'
modified: '2023-11-20T13:08:56.822Z'
---

# bash shopt

> set and unset shell options

    Change the setting of each shell option OPTNAME.  Without any option
    arguments, list each supplied OPTNAME, or all shell options if no
    OPTNAMEs are given, with an indication of whether or not each is set.


Historically, the `set` was used to turn options on and off. As the number of options grew, `set` became more difficult to use because options are represented by single letter codes. 
As a result, bash provides the `shopt` command to turn options on and off by name instead of a letter. 

## option

```sh
-o        # restrict OPTNAMEs to those defined for use with `set -o'
-p        # print each shell option with an indication of its status
-q        # suppress output
-s        # enable (set) each OPTNAME
-u        # disable (unset) each OPTNAME
```

## usage

```sh
shopt    | column -t      # print all options as "on" or "off"
shopt -p | column -t      # print all options as "-s" or "-u"

shopt -p cdspell        # same as `unset -u`
shopt -p promptvars     # same as `set -s`

shopt -s histappend     # closing session will appended to HISTFILE rather than overwriting it
```

## see also

- [[bash]]
- [[bash set]]
- [[bash unset]]
- [[bash history]]
- [[env]]

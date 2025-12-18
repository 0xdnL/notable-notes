---
tags: [shell/bash]
title: bash declare
created: '2019-07-30T06:19:48.996Z'
modified: '2025-10-26T13:30:36.305Z'
---

# bash declare

> set variable values and attributes

## option

```sh
# print all values of one type
-xp         # exported vairables
-f          # list sourced functions
-F          # list only function names
-p          # show variables
-a          # variables are treated as arrays

-a          # array
-A          # variables are treated as associative arrays
-f          # uses funtion names only
-F          # displays function names without definitions
-i          # the variables are treaded as integers
-r          # makes the variables read-only
-x          # marks the variables for export via the environment
```

## usage

```sh
declare -r foo=bar        # readonly

declare | grep foo      # foo=bar
```

## export

```sh
declare -x var=$value   # bash specific 

export VAR=value        # posix
```

[[bash export]]

## arrays

```sh
declare -a ARRAY=('aa' 'bb' 'cc' 'dd' 'ee')

declare -A ASSOC_ARRAY=([a]=a/string-value [b]=b/string-value)    # associative array

declare | grep ARRAY        # print array and indexes
declare | grep ASSOC_ARRAY  # print array and keys
```

[[bash array]], [[bash readarray]]

## see also

- [[bash export]]
- [[bash set]], [[bash unset]]
- [[bash typeset]]
- [[bash function]]
- [declareref - tldp.org](http://tldp.org/LDP/abs/html/declareref.html)

---
tags: [coreutils]
title: tr
created: '2019-07-30T06:19:49.255Z'
modified: '2025-12-17T12:36:36.812Z'
---

# tr

> translate characters

## option

```sh
-C      # complement set of characters in string1, "-C ab" includes every character except for ‘a’ and ‘b’
-c      # Same as -C but complement the set of values in string1
-d      # delete characters in string1 from the input
-s      # squeeze multiple occurrences of the characters listed in the last operand (either string1 or string2) in the input into a single instance of the character
-u      # guarantee that any output is unbuffered
```

## usage

```sh
tr [-Ccsu] string1 string2
tr [-Ccu] -d string1
tr [-Ccu] -s string1
tr [-Ccu] -ds string1 string2


echo "string" | tr '[:upper:]' '[:lower:]'  # translate all upercase to lowercase

echo $PS1 | tr ':' '\n'

tr -d '\n'    # remove new line character \n


tr '[:upper:]' '[:lower:]' <<EOF    # print batch in lowercase
VARIABLE_A
VARIABLE_N
VARIABLE_X
EOF
```

## see also

- [[cut]]
- [[sed]]
- [[seq]]
- [[bash echo]]
- [[bash parameter expansion]]
- [[openssl]]

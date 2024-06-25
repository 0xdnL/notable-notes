---
tags: [linux]
title: od
created: '2019-09-04T06:17:03.101Z'
modified: '2024-05-02T06:34:20.703Z'
---

# od

> `octal dump` - decimal, hex, [[ascii]] dump

## option

```sh
-b FILE     # displays contents of input in octal format
-c FILE     # displays contents of input in character format

-N 1        # read one byte from /dev/urandom
-An         # means Address none
-t T        # select a type
            #  d - signed decimal
            #  u - unsigned decimal
            #  C - of size (one) char
```

## usage

```sh
od -An -c FILE        # displays the contents of input in character format but with no offset information

od -c -               # accept input from STDIN

echo '"' | tr -d "\n" | od -An -t uC  # print/get decimal-set

od -An -td -N1 /dev/urandom      # dump random character

var="$(echo -n '☠' | od -An -tx1)"; printf '\\x%s' ${var^^}; echo

echo -n '"' | od -An -t uC   # get decimal-set
#                       └────────────────  Use od (octal dump) to print:
#                                              -An    means Address none
#                                              -t     select a type
#                                                  u  type is unsigned decimal.
#                                                  C  of size (one) char
```

## unicode characters

```sh
# The character U+a789 "꞉" could be confused with the ASCII  character U+003a ":", which is more common in source code

printf "bash true false :" | od -An -t x1
 62 61 73 68 20 74 72 75 65 20 66 61 6c 73 65 20
 3a

printf "bash true false ꞉" | od -An -t x1
 62 61 73 68 20 74 72 75 65 20 66 61 6c 73 65 20
 ea 9e 89

echo -e '\ua789'
echo -e '\u003a'
```

## see also

- [[ascii]]
- [[xxd]]
- [[hexdump]]
- [[rl]]
- [[tr]]
- [[bash echo]]
- [[bash printf]]
- [[ascii]]

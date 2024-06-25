---
tags: [linux]
title: xxd
created: '2019-09-04T06:14:01.648Z'
modified: '2024-05-02T06:33:37.285Z'
---

# xxd

> make a hexdump or do the reverse

## install

```sh
brew install vim            # part of vim for some reaseon ?!
```

## option

```sh
-a              # toggle autoskip: A single '*' replaces nul-lines    Default off
-b              # binary digit dump (incompatible with -ps,-i,-r)     Default hex
-C              # capitalize variable names in C include file style (-i)
-c COLS         # format COLS octets per line                         Default 16 (-i: 12, -ps: 30)
-E              # show characters in EBCDIC                           Default ASCII
-e              # little-endian dump (incompatible with -ps,-i,-r)
-g BYTES        # number of octets per group in normal output         Default 2 (-e: 4)
-h              # print this summary
-i              # output in C include file style
-l LEN          # stop after <len> octets
-n NAME         # set the variable name used in C include output (-i)
-o off          # add <off> to the displayed file position
-ps             # output in postscript plain hexdump style
-r              # reverse operation: convert (or patch) hexdump into binary
-r -s off       # revert with <off> added to file positions found in hexdump
-d              # show offset in decimal instead of hex
-s [+][-]seek   # start at <seek> bytes abs. (or +: rel.) infile offset
-u              # use upper case hex letters
-v              # show version: "xxd 2022-01-14 by Juergen Weigert et al."
```

## usage

```sh
echo "STRING" | xxd       # get hex of string

xxd docker-compose.yml    # hexdump file

xxd -plain                # output in postscript continuous hexdump style. Also known as plain hexdump style.

echo '0 4a' 
echo '0x4a' | xxd -r
# xxd -r <<<'0 4a'          # decimal


echo -n "bash true false :" | xxd -p
6261736820747275652066616c7365203a

echo -n "bash true false ꞉" | xxd -p
6261736820747275652066616c736520ea9e89
```

## see also

- [[od]]
- [[vim]]
- [[brew]]
- [[ascii]]
- [[hexdump]]
- [[bash echo]]

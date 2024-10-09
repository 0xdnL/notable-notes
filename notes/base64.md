---
tags: [linux]
title: base64
created: '2020-09-01T08:26:05.388Z'
modified: '2024-09-19T09:13:37.603Z'
---

# base64

> encode and decode using base64 representation

## option

```sh
                  -w column         # wrap encoded output after column
--input=input,    -i input          # read input from input.  The default is stdin; passing “-” also represents stdin.
--output=output,  -o output         # write output to output_file.  The default is stdout; passing “-” also represents stdout.
```

## usage

```sh
base64 -w 0 FILE      # encode in single line

base64 -i IN_FILE -o OUT_FILE

echo FOO | python -m base64
```

## see also

- [[jq]] `@base64d`
- [[echo]]
- [[openssl]]
- [[python]]
- [[baudot]]

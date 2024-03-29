---
tags: [linux]
title: iconv
created: '2020-03-16T16:29:57.096Z'
modified: '2023-12-06T12:08:26.152Z'
---

# iconv

> convert some text in one encoding into another encoding

## option

```sh
-f FROM,  –from-code=FROM    # use FROM encoding for input characters
-t TO,    –to-code=TO        # use TO encoding for output characters
-l,       –list              # list all known character set encodings
-c                           # silently discard characters that cannot be converted instead of terminating when encountering such characters
-o OUT,   –output=OUT        # use outputfile for output
          -verbose           # print progress information on standard error when processing multiple files
```

## usage

```sh
iconv -f encoding -t encoding FILE -o OUTPUTFILE

echo abc ß ? € à?ç | iconv -f UTF-8 -t ASCII//TRANSLIT
```

## see also

- [[file]]
- [[ffmpeg]]
- [[ascii]], [[unicode]]

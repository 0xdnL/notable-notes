---
tags: [json, rust]
title: jless
created: '2022-05-17T19:12:45.216Z'
modified: '2024-11-12T09:48:07.835Z'
---

# jless

>  json viewer for reading, exploring, and searching through json data

## install

```sh
brew install jless

cargo install jless
```

## option

```sh
-h, --help                     # print help information
-m, --mode MODE                # initial viewing mode. 
                               # --mode line  opening and closing curly and square brackets are shown and all Object keys are quoted
                               # --mode data (default), closing braces, commas, and quotes around Object keys are elided. 
                               # active mode can be toggled by pressing 'm' [default: data]
    --scrolloff SCROLLOFF      # number of lines to maintain as padding between the currently focused row and the top or bottom of the screen. Setting this to a large value will keep the focused in the middle of the screen (except at the start or end of a file) [default: 3]
-V, --version                  # print version information
    --json                     # parse input as JSON, regardless of file extension
    --yaml                     # parse input as YAML, regardless of file extension
```

## usage

```sh
alias yless="jless --yaml"

cat file.json | jless
```

## Copying and Printing

```sh
yy, pp    # copy/print the value of the currently focused node, pretty printed
yv, pv    # copy/print the value of the currently focused node in a "nicely" printed one-line format
ys, ps    # if currently focused value is a string, copy/print the contents of the string unescaped (except control characters)
yk, pk    # copy/print the key of the current key/value pair
yp, pP    # copy/print the path from the root JSON element to the currently focused node, e.g., .foo[3].bar
yb, pb    # like yp, but always uses the bracket form for object keys, e.g., ["foo"][3]["bar"], which is useful if the environment where you'll paste the path doesn't support the .key format, like in Python
yq, pq    # copy/print a jq style path that will select the currently focused node, e.g., .foo[].bar 
```

## see also

- [[less]]
- [[jq]]
- [[fx]]
- [[cargo]]
- [jless.io](https://jless.io/)

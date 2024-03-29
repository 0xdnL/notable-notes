---
tags: [c]
title: tcl
created: '2020-02-25T07:16:45.951Z'
modified: '2023-03-24T09:51:49.499Z'
---

# tcl

> `"tickle"`/`"tee cee ell"` - `tool command language`
> multi-purpose `c` library which includes a powerful dynamic scripting language, high-level, general-purpose, interpreted

## install

```sh
brew cask install tcl
```

## usage

```sh
tclsh    # start tcl shell
```

## tcl shell

```tcl
puts $tcl_version     # prints tcl version

puts [ls -l]          # square-bracket used for command substitution
```

## script

```tcl
#!/usr/bin/tclsh

set variableA 10
set {variable B} test
puts $variableA
puts ${variable B}
```

## see also

- [wiki.tcl-lang.org/page/What+is+Tcl](https://wiki.tcl-lang.org/page/What+is+Tcl)
- [tcl-lang.org/man/tcl8.5/tutorial/tcltutorial.html](https://www.tcl-lang.org/man/tcl8.5/tutorial/tcltutorial.html)
- [[lua]]
- [[sam]]

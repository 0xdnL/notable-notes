---
tags: [go]
title: language go
created: '2023-11-28T10:22:46.407Z'
modified: '2024-01-11T12:44:20.775Z'
---

# language go

## language

```
  has                             doesn't have

+ package system                - implicit numeric conversion
+ first-class-functions         - constructors/destructors
+ lexical-scope                 - operator overloading
+ system call interface         - default parameter values
+ immutable string in utf-8     - inheritance (type-based inheritance → subclasses)
+ struct ~ class                - generics    `parametrics polimorphism` ≈ `generics`
+ concurrency support (CSP)     - exceptions
                                - macros
+ `garbage collected`           - function annotations
+ it's `staticallly typed`      - thread local storage
                                - inheritance but composition of type
                                - explicit declaration, interface-implementation required
```

## semicolon rule

> `;` terminates statements

if last token before new line:
- is an `identifiere`   -> `int`, `float64`
- is an `basic literal` -> `number`, `string`
- is a `token`          -> `break`, `continues`, `fallthrough`, `return`, `++`, `--`, `)`, `}`

if the new line comes after a `token` that could end the statement => insert `;`

## runes atoi itoa

> `runes` are unicode codepoints

## strinconversion Atoi / Itoa

```go
n := strconv.Atoi(os.Args[1])             # converst a string to integer
n := strconv.ParseInt(os.Args[1], 10, 0)
```

## see also

- [[go]]

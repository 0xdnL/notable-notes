---
tags: [java]
title: scala
created: '2019-08-20T07:27:47.862Z'
modified: '2023-03-23T08:44:35.706Z'
---

# scala

> high-level [[jvm]] language which combines object-oriented and functional programming

## usage

```sh
scala     # start repl
```

```scala
:help    // help command

:reset   // clear past commands in session

:type    // print type without evaluating

val x, y = 1

// expressions and string
println(s"Age next year: ${age + 1}")                       // any arbitrary expression can be embedded in ${}
println(s"You are 33 years old: ${age == 33}")
println(s"${hannah.name} has a score of ${hannah.score}")   // use curly braces when printing object fields
```

## see also

- [[sbt]]
- [String interpolation/substitution - alvinalexander.com](https://alvinalexander.com/scala/string-interpolation-scala-2.10-embed-variables-in-strings)
- [[ocaml]]
- [[python]]
- [[java]]

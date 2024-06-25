---
tags: [linux, Notebooks, regex]
title: regex
created: '2019-07-30T06:19:49.223Z'
modified: '2024-01-30T09:23:27.330Z'
---

# regex

> `regular expression` sequence of characters that specifies a match pattern in text

## POSIX 

> `Portable Operating System Interface` includes basic syntax and additional features for character, classes, anchors, quantifiers..)

## POSIX BRE

> Basic Regular Expressions

- default regex notation used in [[bash]]
- includes basic pattern matching with characters such as `.`, `*`, `[]`, `^`, and `$`
- some characters require escaping, such as `\`, `|`, `(`, `)`, `?`, `{`, and `}`

(GNU BRE: GNU Basic Regular Expressions, which are POSIX BRE with GNU extensions     )

## POSIX ERE

> Extended Regular Expressions

- more powerful version of regex notation in [[bash]]
- activated by using the `bash -E` option
- notation supports extended pattern matching features like `+`, `?`, `()`, `{}`, `|`, and `()` without escaping

(GNU ERE: GNU Extended Regular Expressions, which are POSIX ERE with GNU extensions  )

## PCRE

> Perl-Compatible Regex extends the POSIX regex with additional features such as lookahead, lookbehind, named capture groups

[[perl]] Compatible Regular Expressions (c library) 

widely used in programming languages like [[perl]], [[php]], and [[python]]

## javascript

> own regex notation that follows the ECMAScript standard, is similar to PCRE but may have some minor differences

[[javascript]]

## java regex

> uses its own notation, which is similar to POSIX regex but includes additional features like lookbehind and lookaheads

[[java]]

---

## Basic Notations

- Literal Characters: Matching specific characters as they appear.
  Example: `/cat/` matches the word "cat".

## Metacharacters

- Dot (.) - matches any character except newline.
  Example: `/ca./` matches "cat", "cab", "car", etc.
- Asterisk (*) - matches zero or more occurrences of the preceding element.
  Example: `/ca*t/` matches "ct", "cat", "caat", etc.
- Plus (+) - matches one or more occurrences of the preceding element.
  Example: `/ca+t/` matches "cat", "caat", "caaat", etc.
- Question Mark (?) - matches zero or one occurrence of the preceding element.
  Example: `/ca?t/` matches "ct" or "cat".
- Square Brackets ([]) - matches any one character inside the brackets.
  Example: `/[bd]og/` matches "bog" or "dog".
- Pipe (|) - acts as an OR operator to match either the preceding or succeeding element.
  Example: `/hello|hi/` matches either "hello" or "hi".

## Character Classes

- \d - matches any digit character.
  Example: `/\d+/` matches one or more digits.
- \w - matches any word character (alphanumeric and underscore).
  Example: `/\w+/` matches one or more word characters.
- \s - matches any whitespace characters (space, tab, newline).
  Example: `/\s+/` matches one or more whitespace characters.

## Anchors

- ^ - matches the start of a line or string.
  Example: `/^hello/` matches "hello" if it appears at the start.
- $ - matches the end of a line or string.
  Example: `/world$/` matches "world" if it appears at the end.

## Patterns

```
[^="]++(?=")      # explanation
```

## see also

- [[find]]
- [[grep regex]]
- [[bash globbing]]
- [[bash [[]]
- [Regular-Expressions.info - Regexp Patterns](https://www.regular-expressions.info/)
- [Basic vs Extended - gnu.org](https://www.gnu.org/software/grep/manual/html_node/Basic-vs-Extended.html)

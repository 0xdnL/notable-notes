---
tags: [shell/bash/keyword]
title: 'bash [['
created: '2020-09-02T14:24:09.002Z'
modified: '2024-01-30T09:25:44.838Z'
---

# bash \[\[

> execute conditional command - returns a status of `0` or `1`
> EXPRESSION are composed of same primaries used by [[bash test]]

## usage

```sh
[[ EXPRESSION ]]


( EXPRESSION )    # returns value of EXPRESSION
! EXPRESSION      # true if EXPRESSION is false; else false
EXPR1 && EXPR2    # true if both EXPR1 and EXPR2 are true; else false
EXPR1 || EXPR2    # true if either EXPR1 or EXPR2 is true; else false
```

## operators

```sh
EXPR == STRING
EXPR != STRING        # string to the right of operator is used as pattern and pattern matching is performed

STRING =~ REGEX       # string to the right of operator is matched as a extended regex

EXPR1 && EXPR2        # do not evaluate EXPR2 if EXPR1 is sufficient to determine the expression's value
EXPR1 || EXPR2 
```

## example

```sh
CI_COMMIT_BRANCH=cstm-ns-label-1
REGE='([A-Za-z0-9][-A-Za-z0-9_.]*)?[A-Za-z0-9]'

function validate_regex {
  local regex="$1"
  local string="$2"

  if [[ $string =~ $regex ]]; then
      echo "String is valid."
  else
      echo "String is not valid."
  fi
}
```

## see also

- [[regex]]
- [[bash test]]
- [[bash until]]
- [[bash builtin]]

---
title: json5
created: '2024-11-01T11:21:46.170Z'
modified: '2024-11-01T11:25:01.451Z'
---

# json5

> [json5](https://json5.org/) is an extension to the popular [[json]] 

## install

```sh
npm install -g json5 
```

[[npm]]

## usage

```sh
json5 FILE | jq
```

## example json5

```json
{
  // comments
  unquoted: 'and you can quote me on that',
  singleQuotes: 'I can use "double quotes" here',
  lineBreaks: "Look, Mom! \
No \\n's!",
  hexadecimal: 0xdecaf,
  leadingDecimalPoint: .8675309, andTrailing: 8675309.,
  positiveSign: +1,
  trailingComma: 'in objects', andIn: ['arrays',],
  "backwardsCompatible": "with JSON",
}
```

## see also

- [[jq]]
- [[json]]

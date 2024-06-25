---
title: jp
created: '2024-06-05T12:05:51.730Z'
modified: '2024-06-05T12:07:05.320Z'
---

# jp

> command line interface to JMESPath, an expression language for manipulating JSON

## install

```sh
brew install jmespath/jmespath/jp
```

## usage

```sh
echo '{"key": "value"}' | jp key
"value"

echo '{"foo": {"bar": ["a", "b", "c"]}}' | jp foo.bar[1]
"b"
```

## see also

- [[aws]]
- [[jq]]
- [[yq]]

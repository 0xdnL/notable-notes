---
tags: [ruby]
title: ruby symbol
created: '2019-07-30T06:19:49.226Z'
modified: '2024-11-17T10:56:47.644Z'
---

# ruby symbol

> symbols are often used as the equivalent to enums in [[ruby]], as well as keys to a dictionary (hash)

[[tagged union]]

- symbol is immutable
- used in hashes

## usage
```ruby
foo = { :ruby => "red"}

x = :my_str
y = :my_str
# :my_str will only be created once, and x and y point to the same area of memory. On the other hand, if you have

x = "my_str"
y = "my_str"
# a string containing my_str will be created twice, and x and y will point to different instances
```

 ## see also

- [softwareengineering.stackexchange.com/What is a symbol in Ruby?](https://softwareengineering.stackexchange.com/a/24461/276395)
- [[go datastructures]]
- [[yaml]]


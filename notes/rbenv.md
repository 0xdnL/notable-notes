---
tags: [python]
title: rbenv
created: '2021-06-01T13:18:20.553Z'
modified: '2021-06-01T13:43:31.387Z'
---

# rbenv

> `ruby environment` - intercepts `ruby` commands using `shim` executables injected into your `PATH`

## install

> Compatibility note: `rbenv` is incompatible with `rvm` !
```sh
brew install rbenv

rbenv init            # # setup rbenv in shell

rbenv rehash          # after installing new gems

brew upgrade rbenv ruby-build


sudo apt install rbenv
```

## usage
```sh
rbenv install --list

```

## see also
- [github.com/rbenv/rbenv](https://github.com/rbenv/rbenv)
- [[rvm]]
- [[pyenv]]

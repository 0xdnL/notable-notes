---
tags: [shell]
title: asdf
created: '2021-03-29T06:54:55.237Z'
modified: '2025-12-26T10:04:23.420Z'
---

# asdf

> manage multiple language runtime versions on a per-project basis

[[sdk]], [[gvm]], [[nvm]], [[rbenv]],[[pyenv]], [[kubectl]]

## install

```sh
brew install asdf

source "$(brew --prefix asdf)/libexec/asdf.sh"    # append to .bashr
```

## config

```sh
cat $HOME/.tool-versions

ruby 2.5.3
nodejs 10.15.0
```

[asdf-vm.com/manage/configuration](https://asdf-vm.com/manage/configuration.html)

## node

```sh
asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git

asdf list all nodejs

asdf list all nodejs 14

asdf install nodejs latest
```

## kubectl

```sh
asdf plugin-add kubectl   https://github.com/asdf-community/asdf-kubectl.git

asdf list all kubectl

asdf install kubectl 1.24

asdf global kubectl 1.24.17


asdf plugin-add helm      https://github.com/Antiarchitect/asdf-helm.git
asdf plugin-add helmfile  https://github.com/feniix/asdf-helmfile.git
asdf plugin-add kustomize https://github.com/Banno/asdf-kustomize.git
```

[[kubectl]]

## see also

- [[pluto]]
- [[tfswitch]]
- [[sdk]]
- [[nvm]]
- [github.com/asdf-vm/asdf](https://github.com/asdf-vm/asdf)

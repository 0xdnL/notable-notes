---
tags: [linux]
title: gitconfig
created: '2024-02-20T09:28:56.717Z'
modified: '2024-10-08T09:23:35.087Z'
---

# gitconfig

> ini style file containing [[git]] config

## examples

```sh
[alias]
  cpl = !git checkout - && git pull
  cbd = !git checkout -b "update-$(date +%F_%H%M)"

[core]
  editor = vim
  hooksPath = .husky

[init]
  defaultBranch = main

[user]
  name = Some Name
  email = name@mail.com

[remote "origin"]
  gh-resolved = base

[pull]
  ff = only   

[bulkworkspaces]
  WORKSPACE_NAME = PATH
```

```sh
# seperate configs per remote

cat <<EOF > ~/.gitconfig
[includeIf "gitdir:~/gitlab.com/"]
  path = ~/.gitconfig-gitlab

[includeIf "gitdir:~/github.com/"]
  path = ~/.gitconfig-github
EOF

cat <<EOF > ~/.gitconfig-github
[user]
  name  = user
  email = user@mail.com
  signingkey = AAAA1111AAAA1111

[commit]
  gpgsign = true

[push]
  default = simple
EOF
```

## see also

- [[git]]
- [[gpg-agent]]

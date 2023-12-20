---
tags: [container, rust]
title: kubie
created: '2023-10-16T10:43:44.965Z'
modified: '2023-11-17T12:29:06.241Z'
---

# kubie

> shell independent context switching, namespace switching and prompt modification

## install

```sh
brew install kubie
```

## usage

```sh
kubie ctx                       # display a selectable menu of contexts
kubie ctx CONTEXT               # switch the current shell to the given context (spawns a shell if not a kubie shell)
kubie ctx -                     # switch back to the previous context
kubie ctx CONTEXT -r            # spawn a recursive shell in the given context
kubie ctx CONTEXT -n NAMESPACE  # spawn a shell in the given context and namespace

kubie ns              # display a selectable menu of namespaces
kubie ns NAMESPACE    # switch the current shell to the given namespace
kubie ns -            # switch back to the previous namespace
kubie ns NAMESPACE -r # spawn a recursive shell in the given namespace

kubie exec CONTEXT NAMESPACE CMD ARGS..       # execute a command in the given context and namespace
kubie exec WILDCARD NAMESPACE CMD ARGS..      # execute a command in all the contexts matched by the wildcard and in the given namespace
kubie exec WILDCARD NAMESPACE -e CMD ARGS..   # execute a command in all the contexts matched by the wildcard and in the given namespace but fail early if any of the commands executed return a non-zero exit code

kubie edit          # display a selectable menu of contexts to edit
kubie edit CONTEXT  # edit the file that contains this context

kubie edit-config   # edit kubie's own config file

kubie lint          # lint k8s config files for issues

kubie info ctx      # print name of current context
kubie info ns       # print name of current namespace
kubie info depth    # print depth of recursive contexts

kubie update        # will check the latest kubie version and update your local installation if needed
```

## see also

- [[bash prompt]]
- [[kubectx]]
- [[kubens]]
- [[kubectl]]

---
tags: [shell/bash/builtin]
title: bash complete
created: '2019-07-30T06:19:48.994Z'
modified: '2023-11-18T13:00:56.020Z'
---

# bash complete

> specify how arguments are to be completed by readline

## option

```sh
-p        # print existing completion specifications in a reusable format
-r        # remove a completion specification for each NAME, or, if no NAMEs are supplied, all completion specifications
-D        # apply the completions and actions as the default for commands without any specific completion defined
-E        # apply the completions and actions to "empty" commands -- completion attempted on a blank line
-I        # apply the completions and actions to the initial (usually the command) word
```

## usage

```sh
complete -W "word1 word2 .." command    # -W wordlist provide a list of words for completion


complete -A directory dothis           # only directory names

_dothis_completions() {
  COMPREPLY+=("now")                   # array variable used to store the completions        
  COMPREPLY+=("tomorrow")
  COMPREPLY+=("never")
}

complete -F _dothis_completions dothis    # -F flag defining function that will provide the completions
```


## enable autocomplete for alias

```sh
alias k=kubectl
complete -o default -F __start_kubectl k
```

[kubernetes.io/docs/reference/kubectl/cheatsheet/#bash](https://kubernetes.io/docs/reference/kubectl/cheatsheet/#bash)

## see also

- [[bash alias]]
- [[bash compgen]]
- [[gnu readline]]
- [Creating a bash completion script](https://iridakos.com/tutorials/2018/03/01/bash-programmable-completion-tutorial.html)

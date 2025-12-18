---
title: chsh
created: '2025-12-06T22:12:20.300Z'
modified: '2025-12-06T22:18:43.970Z'
---

# chsh


> `chpass`, `chfn`, `chsh` – add or change user database information

- `chpass` utility allows editing of the user database information associated with user or, by default, the current user
- `chpass` utility cannot change the user's password on Open Directory systems, use [[passwd]] instead
- `chfn` and `chsh` utilities behave identically to chpass - There is only one program

## option

```sh
-l location    # If not specified, chpass will perform a search for the user record on all available Open Directory nodes
               # When specified, chpass will edit the user record on the directory node at the given location

-u authname    # user name to use when authenticating to the directory node containing the user

-s newshell    # Attempt to change the user's shell to newshell
```

## usage

```sh
chsh -s /bin/zsh
```


## see also

- [[bash]]


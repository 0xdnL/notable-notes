---
title: wsl
created: '2025-12-22T16:20:55.620Z'
modified: '2025-12-22T16:33:04.613Z'
---

# wsl

> "Windows Subsystem for Linux" run linux environment directly on Windows without vm overhead

[[docker]], [[powershell]]

## option

```sh
--distribution, -d DISTRO   # Run the specified distribution
--user, -u USER             # Run as the specified user
--system                    # Launches a shell for the system distribution
```

## usage

```sh
wsl --install           # Install WSL and the default Ubuntu distribution

wsl --status
wsl --version

wsl --list --online     # list available distros
wsl --list --verbose    # list local wsl distros

wsl ~   #  start in the user's home directory

wsl --distribution DISTRO --user USER

wsl --shutdown
```

## see also

- [learn.microsoft.com/en-us/windows/wsl/install](https://learn.microsoft.com/en-us/windows/wsl/install)
- [learn.microsoft.com/en-us/windows/wsl/basic-commands](https://learn.microsoft.com/en-us/windows/wsl/basic-commands)

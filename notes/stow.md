---
title: stow
created: '2025-10-07T15:58:03.187Z'
modified: '2026-01-22T12:59:25.620Z'
---

# stow

> gnu stow - a symlink farm manager 

## install

```sh
brew    install stow
apt-get install stow
```

## .stow-global-ignore

```sh
# Comments and blank lines are allowed.

RCS
.+,v

CVS
\.\#.+       # CVS conflict files / emacs lock files
\.cvsignore

\.svn
_darcs
\.hg

\.git
\.gitignore
\.gitmodules

.+~          # emacs backup files
\#.*\#       # emacs autosave files

^/README.*
^/LICENSE.*
^/COPYING
```

[gnu.org/.../Types-And-Syntax-Of-Ignore-Lists](https://www.gnu.org/software/stow/manual/html_node/Types-And-Syntax-Of-Ignore-Lists.html)

## option

```sh
-t DIR,   --target=DIR       # Set the target directory to "DIR" instead of the parent of the stow directory.
-D,       --delete           # Unstow the packages that follow this option from the target directory rather than installing them.
-R,       --restow           # first unstow, then stow again, useful for pruning obsolete symlinks from the target tree after updating the software in a package
          --adopt            # if a target is encountered which already exists but is a plain file, then normally Stow will register this as a conflict and refuse to proceed
                             # This option changes that behaviour so that the file is moved to the same relative place within the package's installation image within the stow directory, and then stowing proceeds as before.
                             # So effectively, the file becomes adopted by the stow package, without its contents changing.
```

## usage

```sh
mkdir ~/dotfiles 
mv .bashrc dotfiles/
cd dotfiles/

stow .        # create symlinks for all files in current dir

stow -D .     # unstow the packages in current dir

stow -t ~ .   # use targe ~ to stow to
```

## see also

- [[chezmoi]]
- [[git]]
- [[eza]]
- [[tmux]]
- [[nvim]]

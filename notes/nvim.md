---
tags: [editor, linux, macos]
title: nvim
created: '2023-04-14T09:04:09.667Z'
modified: '2024-11-22T11:42:55.989Z'
---

# nvim

> neo [[vim]]

[neovim.io](https://neovim.io/), [[nvchad]]

## install

```sh
brew install neovim
```

## directories

```sh
$HOME.config/nvim
$HOME.local/state/nvim/
```

## option

```sh
```

## usage

```sh
nvim
```

## key-bindings

```sh
# ⇥=Tab ⇪=Caps Lock. ⇧=Shift ⌃=Control/Ctrl ⌥=Option/Alt ⌘=Command/Cmd ␣=Spacebar
# ↑=UpArrow, ↓=DownArrow, ←=LeftArrow, →=RightArrow

␣ + c + h # open cheet sheet       # U+2423 "Open Box"
␣ + t + h # set nvchad theme
␣ + f + f # find files
␣ + f + b # buffers ≠ tabs

⇥         # next buffer
⇧ + ⇥     # prev buffer
␣ + x     # close buffer
```

## tabs and splits

```sh
:tabnew
:tabnext

:vsp      # vertical split
:sp       # split
⌃ + k     # ↑
⌃ + h     # ←
⌃ + j     # ↓
⌃ + l     # →



:vsp file2.txt
:sp file2.txt

C-w + h # Move to the window to the left
C-w + j # Move to the window below
C-w + k # Move to the window above
C-w + l # Move to the window to the right
C-w + > # Increase the window width
C-w + < # Decrease the window width
C-w + + # Increase the window height
C-w + - # Decrease the window height
```

## lazy.nvim

> a modern plugin manager for Neovim, makes it easy to customize and extend config

```sh
:Lazy       # start lazyvim
```

[github.com/folke/lazy.nvim](https://github.com/folke/lazy.nvim)
[www.lazyvim.org](https://www.lazyvim.org/)

## which-key.nvim

> helps you remember your Neovim keymaps, by showing available keybindings in a popup as you type

```sh

```

[github.com/folke/which-key.nvim](https://github.com/folke/which-key.nvim)

## mason.nvim

```sh
:Mason
:MasonInstallAll

g?
```

[github.com/williamboman/mason.nvim](https://github.com/williamboman/mason.nvim)

## treesitter

```sh
:TSInstallInfo

:TSInstall hcl
```

## nvim-tree

```sh
:NvimTreeOpen
:NvimTreeClose
:NvimTreeToggle

⌃ + n     # nvim-tree / file viewer
⌃ + l     # move right to open file
⌃ + h     # move left to nvim-tree


D         # trash
E         # expand all
H         # toggle filter: dot files
I         # toggle filter: gitignore
O         # open window picker
R         # refresh
S         # search
W         # collapes

a         # new file or directory
g?        # show mapping/help
r         # rename file
m         # mark file
```

[github.com/nvim-tree/nvim-tree.lua](https://github.com/nvim-tree/nvim-tree.lua)
[docs.rockylinux.org/books/nvchad/nvchad_ui/nvimtree/](https://docs.rockylinux.org/books/nvchad/nvchad_ui/nvimtree/)

## telescope

> highly extendable fuzzy finder over lists

```sh
<leader> + fa  # Find all files
<leader> + ff  # Find files
<leader> + th  # Nvchad themes
<leader> + pt  # Pick hidden term
<leader> + gt  # Git status
<leader> + cm  # Git commits
<leader> + fz  # Find in current buffer
<leader> + fo  # Find oldfiles
<leader> + ma  # Find marks
<leader> + fh  # Help page
<leader> + fb  # Find buffers
<leader> + fw  # Live grep

# Mappings 	    Action
<C-n>/<Down> 	# Next item
<C-p>/<Up> 	  # Previous item
j/k 	        # Next/previous (in normal mode)
H/M/L 	      # Select High/Middle/Low (in normal mode)
gg/G 	        # Select the first/last item (in normal mode)
<CR> 	        # Confirm selection
<C-x> 	      # Go to file selection as a split
<C-v> 	      # Go to file selection as a vsplit
<C-t> 	      # Go to a file in a new tab
<C-u> 	      # Scroll up in preview window
<C-d> 	      # Scroll down in preview window
<C-f> 	      # Scroll left in preview window
<C-k> 	      # Scroll right in preview window
<M-f> 	      # Scroll left in results window
<M-k> 	      # Scroll right in results window
<C-/> 	      # Show mappings for picker actions (insert mode)
? 	          # Show mappings for picker actions (normal mode)
<C-c> 	      # Close telescope (insert mode)
<Esc> 	      # Close telescope (in normal mode)
<Tab> 	      # Toggle selection and move to next selection
<S-Tab>       # Toggle selection and move to prev selection
<C-q> 	      # Send all items not filtered to quickfixlist (qflist)
<M-q> 	      # Send all selected items to qflist
<C-r><C-w> 	  # Insert cword in original window into prompt (insert mode)
<C-r><C-a> 	  # Insert cWORD in original window into prompt (insert mode)
<C-r><C-f> 	  # Insert cfile in original window into prompt (insert mode)
<C-r><C-l> 	  # Insert cline in original window into prompt (insert mode)
```

[github.com/nvim-telescope/telescope.nvim](https://github.com/nvim-telescope/telescope.nvim?tab=readme-ov-file#getting-started)

## see also

- [[vim]], [[ed]]
- [[lua]], [[luarocks]]
- [[freedesktop xdg]]
- [[macos keyboard shortcuts]]
- [unicode]]

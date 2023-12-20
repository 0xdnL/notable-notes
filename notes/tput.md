---
tags: [linux]
title: tput
created: '2019-07-30T06:19:49.254Z'
modified: '2023-11-15T09:04:49.917Z'
---

# tput

> initialize a terminal or query terminfo database

## capabilitie

```sh
longname        # Full name of the terminal type
lines           # Number of lines in the terminal
cols            # Number of columns in the terminal
colors          # Number of colors available
sc 	            # ave the cursor position
rc 	            # estore the cursor position
home            # Move the cursor to upper left corner (0,0)
cup ROW COL   	# Move the cursor to position row, col
cud1 	          # ove the cursor down 1 line
cuu1 	          # ove the cursor up 1 line
civis 	        # Set to cursor to be invisible
cnorm 	        # Set the cursor to its normal state

setaf VALUE 	  # set foreground color
setab VALUE 	  # set background color
```

## usage

```sh
tput cup 0 0      # send sequence to move the cursor to row 0, column 0 (upper left corner of the screen, aka "home" cursor position)
tput cup 5 20     # move the cursor to the position 20 characters to the right and 5 rows down

tput clear        # echo the clear-screen sequence for the current terminal.

tput cols         # print the number of columns for the current terminal.

tput longname     # prints term longname  e.g. "VT 100/ANSI X3.64 virtual terminal"


tput setaf 2; echo '${LBC_VERSION} has been set.'       # print in green
tput setaf 1; echo '${LBC_VERSION} has NOT been set.'   # print in red

tput setaf 0      # BLACK
tput setaf 1      # RED
tput setaf 2      # GREEN
tput setaf 3      # YELLOW
tput setaf 4      # BLUE
tput setaf 5      # MAGENTA
tput setaf 6      # CYAN
tput setaf 7      # WHITE
tput setaf 8 	    # not used
tput setaf 9 	    # reset to default color
tput setaf 190    # LIME_YELLOW
tput setaf 153    # POWDER_BLUE
tput bold         # BRIGHT
tput sgr0         # NORMAL
tput blink        # BLINK
tput smso         # REVERSE
tput smul         # UNDERLINE
```

## see also

- [[bash prompt]]
- [[diff]]
- [[infocmp]]
- [LinuxCommand.org: tput](http://linuxcommand.org/lc3_adv_tput.php)

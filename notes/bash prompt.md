---
tags: [shell/bash]
title: bash prompt
created: '2019-07-30T06:19:49.017Z'
modified: '2023-11-17T12:28:56.454Z'
---

# bash prompt

> `man bash` at the section `PROMPTING`

## env

```sh
PS1

PROMPT_DIRTRIM

PROMPT_COMMAND
PROMPT_DIRTRIM=1          # see also prompt PS1="\W"
```

## usage

```sh
PS1="\u@\w:\$"

PS2='> ' # used in multiline commands; linebreak symbol e.g. ">"

# PS3 - select

# PS4 used with 'set -x'
PS4='$0.$LINENO+ '
PS4='+ ${BASH_SOURCE##*/}.${LINENO} ${FUNCNAME}: '


PROMPT_COMMAND='[ $? -eq 0 ] || printf "(╯°□°）╯︵ ┻━┻\n"'  #  flip a table whenever a command return a non-zero exit status
```

## prompt color

```sh
__aws_ps1() {

  local YELLOW="\001$(tput setaf 3)\002"
  local RESET="\001$(tput sgr0)\002"

  printf "{%b} " "${YELLOW}${AWS_PROFILE}${RESET}";
  #echo -e "{${YELLOW}${AWS_PROFILE}${RESET}}";
}

export PS1='$(__aws_ps1)..'
```
[[bash tput]]

## escape sequences

```sh
\a              # an ASCII bell character (07)
\d              # the  date  in "Weekday Month Date" format (e.g., "Tue May 26")
\D{format}      # format is passed to strftime(3)  and  the  result  is inserted  into the prompt string; braces are required. e.g. '\D{%F %T}'
\e              # an ASCII escape character (033)
\h              # the hostname up to the first `.'
\H              # the hostname
\j              # the number of jobs currently managed by the shell
\l              # the basename of the shell's terminal device name
\n              # newline
\r              # carriage return
\s              # the  name  of  the shell, the basename of $0 (the portion following the final slash)
\t              # the current time in 24-hour HH:MM:SS format
\T              # the current time in 12-hour HH:MM:SS format
\@              # the current time in 12-hour am/pm format
\A              # the current time in 24-hour HH:MM format
\u              # the username of the current user
\v              # the version of bash (e.g., 2.00)
\V              # the release of bash, version + patch level (e.g., 2.00.0)
\w              # the current working  directory,  with  $HOME  abbreviated with  a tilde (uses the value of the PROMPT_DIRTRIM variable)
\W              # the basename of the current working directory, with $HOME abbreviated with a tilde
\!              # the history number of this command
\#              # the command number of this command
\\$             #  if the effective UID is 0, a #, otherwise a $
\nnn            # the character corresponding to the octal number nnn
\\              # a backslash
\[              # begin  a sequence of non-printing characters, which could be used to embed a terminal  control  sequence  into  the prompt
\]              # end a sequence of non-printing characters
```

```sh
\[    \]    # are only special when you assign PS1
\001  \002  # if print from a function that runs when the prompt use the bytes 
```

[wiki.archlinux.org/title/Bash/Prompt_customization](https://wiki.archlinux.org/title/Bash/Prompt_customizatio)
[http://mywiki.wooledge.org/BashFAQ/053](http://mywiki.wooledge.org/BashFAQ/053)
[https://stackoverflow.com/bash-prompt-and-echoing-colors-inside-a-function](https://stackoverflow.com/a/43462720/14523221)

## see also

- [[bash]]
- [[tput]]
- [[psql]]
- [[kubie]]
- [[bash echo]], [[bash printf]]
- [[bash select]]
- [[bash debugging]]
- [bneijt.nl/add-a-timestamp-to-your-bash-prompt/](https://bneijt.nl/blog/post/add-a-timestamp-to-your-bash-prompt/)
- [My new favorite Bash prompt - BrettTerpstra.com](http://brettterpstra.com/2009/11/17/my-new-favorite-bash-prompt/)

---
tags: [shell/bash]
title: bash redirects
created: '2019-07-30T06:19:49.011Z'
modified: '2025-05-09T09:08:10.326Z'
---

# bash redirects

[[bash]]

## usage

```sh
>     # Output Redirection          - Redirects STDOUT to a file, overwriting the file if it exists
>>    # Append Output Redirection   - Redirects STDOUT to a file, appending the output to the file if it exists
<     # Input Redirection           - Redirects the content of a file to the standard input STDIN of a command

1>    # STDOUT Redirection
2>    # STDERR Redirection          - Redirects the standard error STDERR output to a file, overwriting the file if it exists
&>    # Redirect STDOUT and stderr  - Redirects both standard output STDOUT and standard error STDERR to a file, overwriting the file if it exists
>>&   # Append STDOUT and stderr    - appends both STDOUT and stderr to a file instead of overwriting it
2>&1  # Redirect stderr to STDOUT   - Redirects standard error STDERR to the same destination as standard output STDOUT

<()   # Process Substitution        - Replaces the command with a temporary file that contains the output of the command
|     # Pipe                        - Redirects STDOUT of one command to the standard input STDIN of another command

echo "Hello" > file.txt
echo "World" >> file.txt`
grep "Hello" < file.txt
ls non_existing_file 2> error.txt
command &> output.txt
command >>& output.txt
command > output.txt 2>&1
diff <(command1) <(command2)
echo "Hello" | grep "H"



>|FILE               # forces STDOUT to FILE even if noclobber is set

n>|FILE              # forces output to FILE from FILE descriptor n even if noclobber is set

<> FILE              # uses FILE as both STDIN and STDOUT

n<>FILE              # uses FILE as both input and output for file descriptor n
```

## pipe

> Redirects STDOUT of one command to the standard input STDIN of another command

```sh
command | cat

command_which_exit_10 | command_which_exit_1      
echo "${PIPESTATUS[0]} ${PIPESTATUS[1]}"        # get $? from commands

# see also
set -o pipefail
```

[[bash set]]

```sh
 mkfifo pipe
 tee out.txt < pipe &
 command > pipe
 echo $?
```

[stackoverflow.com/pipe-output-and-capture-exit-status-in-bash](https://stackoverflow.com/a/1221844/14523221), [[mkfifo]]


## process substitution

> process substiution feeds the output of a process (or processes) into the stdin of another process.
> process substitution uses `/dev/fd/<n>` files to send the results of the process(es)

```sh
>(COMMAND_LIST)

<(COMMAND_LIST)

echo >(true)
/dev/fd/63

echo <(true)
/dev/fd/63
```

[[bash read]]
[tldp.org/.../process-sub.html](http://tldp.org/LDP/abs/html/process-sub.html)
[what-is-the-portable-posix-way-to-achieve-process-substitution](https://unix.stackexchange.com/questions/309547/what-is-the-portable-posix-way-to-achieve-process-substitution)


## here-doc

```sh
[n]<<[-]WORD         # here-document
  here-document
DELIMITER

echo <<EOF> FILE
Hello World
EOF
```

[[echo]], [[cat]], [[yq]]

## here-string

```sh
[n]<<< word          # here-string
```

```sh
<()                  # process substitution
< <()                  # process substitution

n>FILE               # directs FILE descriptor n to FILE
n<FILE               # takes FILE descriptor n from FILE
n>>FILE              # directs FILE description n to FILE; append to file if it already exists

&[FILEDESCRIPTOR]     # reference to value of filedescriptor

n>&                  # duplicates STDOUT to file descriptor n
n<&                  # duplicates STDIN from file descriptor n
n>&m                 # file descriptor n is made to be a copy of the output file descriptor
n<&m                 # file descriptor n is made to be a copy of the input file descriptor
&>FILE               # directs STDOUT and standard error to FILE

<&-                  # closes the STDIN
>&-                  # closes the STDOUT
n>&-                 # closes the ouput from FILE descriptor n
n<&-                 # closes the input from FILE descripor n


&>/dev/null         # shorthand for `1> /dev/null 2> /dev/null`

command 1>&- 2>&-           # http://www.cyberciti.biz/faq/how-to-redirect-output-and-errors-to-devnull/#comment-40252
job 1>&- 2>&-  &            # additional & at end of job to put it in backgrounds
command 1>&- 2>&-  &        # additional & at end of command to put it in backgrounds
```

## dash

> redirection from STDIN to STDOUT or STDOUT to STDIN

```sh
cat -                           # redirects from STDIN to STDOUT
echo "whatever" | cat -         # redirects from STDIN to STDOUT
grep "foo" FILE | diff FILE2 -
```

## see also

- [[tee]]
- [[tar]]
- [[wc]]
- [[heredoc]]
- [[bash read]]
- [[bash readarray]]
- [[bash history]]
- [[bash exec]]
- [tldp.org/special-chars.html](http://tldp.org/LDP/abs/html/special-chars.html#DASHREF2)

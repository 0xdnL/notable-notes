---
tags: [linux]
title: sed
created: '2019-07-30T06:19:49.228Z'
modified: '2024-12-18T11:52:41.912Z'
---

# sed

> `S tream ED itor`

[[awk]], [[grep]]

## install

```sh
brew install gsed
```

## options

```sh
  -n,             --quiet, --silent       # suppress automatic printing of pattern space
                  --debug                 # annotate program execution
  -e script,      --expression=script     # add the script to the commands to be executed
  -f script-file, --file=script-file      # add the contents of script-file to the commands to be executed
                  --follow-symlinks       # follow symlinks when processing in place
  -i[SUFFIX],     --in-place[=SUFFIX]     # edit files in place (makes backup if SUFFIX supplied)
  -l N,           --line-length=N         # specify the desired line-wrap length for the `l' command
                  --posix                 # disable all GNU extensions.
  -E, -r,         --regexp-extended       # use extended regular expressions in the script (for portability use POSIX -E)
  -s,             --separate              # consider files as separate rather than as a single, continuous long stream
                  --sandbox               # operate in sandbox mode (disable e/r/w commands)
  -u,             --unbuffered            # load minimal amounts of data from the input files and flush the output buffers more often
  -z,             --null-data             # separate lines by NUL characters
                  --help                  # display this help and exit
                  --version               # output version information and exit
```

## commands, addressing and flags
    
```sh
s/pattern/replacement/flags # Substitute  - Replaces `pattern` with `replacement`, Flags control the behavior (e.g. `g` for global replacement)
d                           # Delete      - Deletes lines matching the address
p                           # Print       - Prints lines matching the address. Often used with `-n` option to suppress automatic printing
i                           # Insert      - Inserts text before a matched line
a                           # Append      - Appends text after a matched line
c                           # Change      - Replaces the selected line(s) with new text

# addresses: most commands can be prefixed with an address or a range of addresses to specify which lines the command should apply to:
sed '3s/line 3/this is the new line 3/' FILE

# `3` is the address that specifies the third line of the file
# `s` is the substitute command
# `line 3` is the pattern to match
# `this is the new line 3` is the replacement text

#         flags
g       # global        - used with substitute command, without the `g` flag, will only replace the first occurrence of the pattern in each line
i       # ignore case   - makes the search pattern case-insensitive, used with substitute command
p       # print         - when used with the `-n` option , the `p` flag will print the lines that match the pattern
w FILE  # write to FILE - used to write the lines that match a pattern to a FILE
d       # delete        - not a flag, the `d` command is used to delete lines that match a pattern or fall within a specified range
n       # next          - used to read the next input line, replacing the pattern space with the next line of input

sed 's/find/replace/g' FILE               # replaces all occurrences of "find" with "replace" in each line of `FILE`

sed 's/find/replace/gi' FILE              #  all occurrences of "find" (ignoring case, so "Find", "FIND", etc., will also match) with "replace" in each line of `FILE`

sed -n 's/find/replace/p' FILE            # replaces "find" with "replace" in `FILE` and prints only the lines where the substitution was made

sed 's/find/replace/gw output.txt' FILE   # replaces "find" with "replace" in all occurrences in each line of `FILE` and writes the lines where substitutions were made to `output.txt`

sed '/pattern/d' FILE                     # deletes lines that contain "pattern" from `FILE`

sed 'n;d' FILE                            # will delete every other line starting from the second line of the file
```

[learnbyexample.github.io/learn_gnused/flags](https://learnbyexample.github.io/learn_gnused/flags.html)

## usage

```sh
sed "${NUM}q;d" FILE                          # print line from file

sed -n "2p"                                   # print second line only

sed -n '2{p;q}' FILE                          # in case there will be no more line 2 after line 2, spare pointless processing by `q`uitting after `p`rinting

sed -i '4d' FILE                              # delete line 4
sed    '/STRING/d' FILE                       # delete line containing STRING
sed -i '/2018-01-30/!d' FILE                  # delete all lines except ones matching pattern

sed '/INCLUDE/ r foo.h'                       #  insert foo.h after 'INCLUDE'
```

## substitution

```sh
echo 'KEY: VALUE' | sed 's/: /='              # KEY=VALUE

sed -i.tmp 's/^/\t/' *.txt                    # keep copy with extension .tmp   .. osx must provide an extension !
                                              # -i, --in-place
sed -i ''  's/^/\t/'  *.txt                   # without creating a backup, you can use

sed -i '5s/#/\/\//' vector-out-of-bounds.cpp  # in line 5 substitute '#' with '//'

sed -i 's/\(^ExecStart=\).*/ExecStart=\/usr\/bin\/dockerd -H tcp:\/\/0.0.0.0:2375/' /lib/systemd/system/docker.service

sed -i 's/\(^#DOCKER_OPTS=\).*/DOCKER_OPTS="-H tcp:\/\/0.0.0.0:2375"/' /etc/default/docker


echo "<b>foo</b>bar" | sed 's/<.*>//g'      #     greedy matching: "bar"
echo "<b>foo</b>bar" | sed 's/<[^>]*>//g'   # non greedy matching: "foobar"
```

## remove special characters

```sh
sed -r "s/[[:cntrl:]]\[[0-9]{1,3}m//g"        # remove colors from output

sed 's/[^a-zA-Z0-9]//g'                       # remove non-alphanumeric characters
```


## delimiters

```sh
sed -i "s%\$$1%${val}%g" CONF_FILE                                 # % as delimiter to avoid escaping slashes in URLs

sed -n -e 's,.*/bin/sh -c #(nop) \(MAINTAINER .*[^ ]\) *0 B,\1,p'  # , as delimiter to avoid escaping slashed in PATH
```

## pretty print

```sh
# pretty print golang object notation
echo 'core.PodTemplateSpec{ObjectMeta:v1.ObjectMeta{Name:"", GenerateName:""}}' | sed -e 's/{/{\n  /g' -e 's/, /,\n  /g' -e 's/}/\n}/g'
```

## see also

- [[nvim]]
- [[tr]]
- [[cut]]
- [grymoire.com/Unix/Sed](http://www.grymoire.com/Unix/Sed.html)
- [0x2a.at/blog/2008/07/sed--non-greedy-matching](https://0x2a.at/blog/2008/07/sed--non-greedy-matching/)
- [github.com/adrianscheff/useful-sed](https://github.com/adrianscheff/useful-sed)

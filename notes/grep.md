---
tags: [linux]
title: grep
created: '2019-07-30T06:19:49.077Z'
modified: '2024-11-29T12:26:02.953Z'
---

# grep

> derived from [[ed]] operation `g`/`re`/`p` - file pattern searcher

## option

```sh
-s, --no-messages              # suppress error messages
-v, --invert-match             # select non-matching lines
```
###  output control

```sh
-m, --max-count=NUM           # stop after NUM selected lines
-n, --line-number             # print line number with output lines
    --line-buffered           # flush output on every line
-H, --with-filename           # print file name with output lines
-h, --no-filename             # suppress the file name prefix on output
    --label=LABEL             # use LABEL as the standard input file name prefix
-o, --only-matching           # show only nonempty parts of lines that match
-q, --quiet, --silent         # suppress all normal output
    --binary-files=TYPE       # assume that binary files are TYPE: 'binary', 'text', or 'without-match'
-a, --text                    # equivalent to --binary-files=text
-I                            # equivalent to --binary-files=without-match
-d, --directories=ACTION      # how to handle directories; ACTION: 'read', 'recurse', or 'skip'
-D, --devices=ACTION          # how to handle devices, FIFOs and sockets; ACTION: 'read' or 'skip'
-r, --recursive               # like --directories=recurse
-R, --dereference-recursive   # likewise, but follow all symlinks
    --include=GLOB            # search only files that match GLOB (a file pattern)
    --exclude=GLOB            # skip files and directories matching GLOB
    --exclude-from=FILE       # skip files matching any file pattern from FILE
    --exclude-dir=GLOB        # skip directories that match GLOB
-L, --files-without-match     # print only names of FILEs with no selected lines
-l, --files-with-matches      # print only names of FILEs with selected lines
-c, --count                   # print only a count of selected lines per FILE
-T, --initial-tab             # make tabs line up (if needed)
-Z, --null                    # print 0 byte after FILE name
```

### Pattern selection and interpretation

```sh
-E, --extended-regexp         # PATTERNS are extended regular expressions
-F, --fixed-strings           # PATTERNS are strings
-G, --basic-regexp            # PATTERNS are basic regular expressions
-P, --perl-regexp             # PATTERNS are Perl regular expressions
-e, --regexp=PATTERNS         # use PATTERNS for matching
-f, --file=FILE               # take PATTERNS from FILE
-i, --ignore-case             # ignore case distinctions
-w, --word-regexp             # match only whole words
-x, --line-regexp             # match only whole lines
-z, --null-data               # a data line ends in 0 byte, not newline
```

### basic regex

```sh
^        (Caret)              # match expression at the start of a line, as in `^A`
$        (Question)           # match expression at the end of a line, as in `A$`  
\        (Back Slash)         # turn off the special meaning of the next character, as in `\^`.
[ ]      (Brackets)           # match any one of the enclosed characters, as in [aeiou]. Use Hyphen "-" for a range, as in `[0-9]`
[^ ]                          # match any one character except those enclosed in `[ ]`, as in `[^0-9]`
.        (Period)             # match a single character of any value, except end of line.  
*        (Asterisk)           # match zero or more of the preceding character or expression.
\{x,y\}                       # match x to y occurrences of the preceding.   
\{x\}                         # match exactly x occurrences of the preceding.
\{x,\}                        # match x or more occurrences of the preceding.
```

## usage

```sh
cat conf | grep .                         # pattern matches any character except a newline, ignore completely empty

find | grep 'pattern' FILE /dev/null      # show filename with find !

grep -l 'pattern' FILE                    # show only matching filename

grep "^[^#;]" smb.conf                    # filter-out-comments - http://unix.stackexchange.com/a/60995

ls -l | grep "^d"                         # list directories

ps aux | grep "[d]ockerd"                 # avoid grep in output via regex: find character 'd' followed by 'ockerd'

grep -E '192.168.(230.0|231.128)'         # regular expression

grep -E "^[[:alpha:]]*:" Makefile         # get tasks frome makefile

env | grep -E "VAULT_.+=.+"               # get set env variables


echo "http://foo.net/path/repo.git" | \
  grep -o -P '(?<=https:\/\/|http:\/\/|@).*?(?=(\/|:))'   # pcre


echo "${CF_STACKS[*]}" | \
  grep -f <(printf '%s\n' "${CDK_STACKS[@]}") -c          # check array against pattern from file and return count
```

## see also

- [[grepcidr]]
- [[wc]]
- [[pkill]]
- [[nginx]]
- [[regex]]
- [REGEX Cheat Sheet](https://staff.washington.edu/weller/grep.html)
- [Regular Expressions in grep](http://www.robelle.com/smugbook/regexpr.html)
- [ntu.edu.sg/home/ehchua/programming/howto/Regexe](https://www.ntu.edu.sg/home/ehchua/programming/howto/Regexe.html)
- [zwischenzugs.com/2022/02/02/grep-flags-the-good-stuff/](https://zwischenzugs.com/2022/02/02/grep-flags-the-good-stuff/)


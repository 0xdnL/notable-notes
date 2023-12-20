---
tags: [shell/bash/keyword]
title: bash function
created: '2019-07-30T06:19:49.008Z'
modified: '2023-12-08T13:14:06.182Z'
---

# bash function

> keyword `function` defines a shell function

## variables and positional parameters

> the function refers to passed arguments by position as positional parameters

```sh
$@                # expands positional params to seperate words: `$1` `$2`..`$N`
$*                # expands positional params to one words: `$1c$2c..` `c` is the first character of `IFS`
$#                # holds the number of positional parameters.

${FUNCNAME[0]}    # current function
${FUNCNAME[1]}    # parent function
${FUNCNAME[2]}    # so on and so forth
${FUNCNAME[@]}    # all functions including parents
```

## usage

```sh
function sucess () {
  return 0;
}

function fail () {
  return -1;
}

function get_string() {
  echo "string";  # return value is 0
}

echo_string() {
  : ${1?' You forgot to supply a string'}
  echo "${1}";
}


foo() {
  ${1? ERROR Function: ${FUNCNAME[0]}() Usage: " ${FUNCNAME[0]} PARAM"}
}

func() { 
  for arg; do   # without `in` cycle through positional arguments
    echo $arg; 
  done  
}    
```

## declare and unset

```sh
unset -f functname  # deletes a function definition

declare -f          # displays all defined functions in your login session
```

## run function as subshell

```sh
func() (
  echo 0;
)
```

## poor man's bash database

```sh
db_set() { 
  echo "$1,$2" >> database; 
}

db_get() {
  grep "^$1," database | sed -e "s/^$1,//" | tail -n 1; 
}
```

[[grep]], [[sed]], [[tail]]

## see also

- [[bash]]
- [[bash declare]], [[bash unset]]
- [[bash return]]
- [[bash local]]
- [[bash parameter expansion]]
- [arguments - What is $@ in Bash? - Stack Overflow](https://stackoverflow.com/a/3898681/2087704)
- [Log-structured storage - Julia Evans](https://jvns.ca/blog/2017/06/11/log-structured-storage/)

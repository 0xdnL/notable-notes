---
tags: [shell/bash/keyword]
title: bash for
created: '2019-07-30T06:19:49.007Z'
modified: '2023-11-20T18:17:59.320Z'
---

# bash for

> execute commands for each member in a list

## usage

```sh
for name [in words]; do
  command $name;
done

f(){ for arg; do echo $arg; done }    # without `in` cycle thorugh positional arguments

```

## set

```sh
set 1 2 3
for i do echo "$i"; done
```

## seq

```sh
for i in $(seq 1 2 20); do echo "count: $i"; done

```

## range 

```sh
# bash-v4.0+ has inbuilt support for setting up a step value using brace expansion syntax: `{START..END..INCREMENT}` 

for i in {0..10..2}; do echo "count: $i"; done
```

[[brace expansion]]

## three-expression c-style

```sh
for (( EXP1; EXP2; EXP3 )); do echo "test"; done

for (( initialisation ; ending condition ; update )); do
  statements...
done

for (( c=1; c<=5; c++ )); do echo "count: $c"; done
```

[[bash arithmetic expansion]]

## infinite loop

```sh
for (( ; ; )); do echo "infinite loops [ hit CTRL+C to stop]"; done
```

## break

```sh
for I in 1 2 3 4 5; do
  STATEMENT1     
  if (disaster-condition); then
	  break    	         # Abandon the loop.
  fi
  STATEMENT3          #While good and, no disaster-condition.
done
```

## continue

```sh
for f in $FILES ; do
	if [ -f ${f}.bak ];	then      # if .bak backup file exists, read next file
		echo "Skiping $f file..."
		continue                    # read next file and skip the cp command
	fi
	cp $f $f.bak                  # make a backup
done
```

## loop through files

```sh
IFS=$'\n'; # split on NL only, so iterating over files containing spaces would be safe
for F in $(ls -1 webm/*); do 
  echo $F;
done
```

## see also

- [[seq]]
- [[bash ifs]]
- [[bash while]]
- [[bash braces]]
- [[bash function]]
- [[xargs]]
- [Bash "for" loop without a "in foo bar..." part - Unix & Linux Stack Exchange](https://unix.stackexchange.com/a/417296/193945)
